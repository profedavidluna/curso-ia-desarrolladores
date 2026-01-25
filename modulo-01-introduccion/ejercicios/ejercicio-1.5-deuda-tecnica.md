# 🧪 Ejercicio 1.5: Disminuir Deuda Técnica - Tests Unitarios con IA

**Duración**: 40 minutos  
**Dificultad**: Media-Alta  
**Herramienta**: GitHub Copilot / ChatGPT / Claude

---

## 🎯 Objetivos

- Usar IA para generar tests unitarios comprehensivos
- Identificar casos edge que no se habían considerado
- Mejorar cobertura de código existente
- Aprender a escribir tests mantenibles

---

## 📚 Importancia de los Tests Unitarios

Los tests unitarios son esenciales por varias razones:

- ✅ **Detección Temprana de Bugs**: Atrapar errores durante el desarrollo en lugar de en producción
- ✅ **Documentación**: Los tests sirven como documentación de cómo debe funcionar el código
- ✅ **Confianza en Refactorización**: Asegura que los cambios no rompan funcionalidad existente
- ✅ **Desarrollo Más Rápido**: Aunque escribir tests toma tiempo inicialmente, acelera el desarrollo a largo plazo

---

## 📋 Caso de Estudio: Sistema de Procesamiento de Pagos Sin Tests

### Contexto

Un sistema crítico de procesamiento de pagos está en producción pero **NO TIENE TESTS**. El equipo tiene miedo de hacer cambios porque no saben si romperán algo.

**Tu misión**: Crear una suite completa de tests.

### Código Sin Tests (TypeScript)

```typescript
export enum PaymentStatus {
    PENDING = 'PENDING',
    COMPLETED = 'COMPLETED',
    FAILED = 'FAILED'
}

export enum PaymentMethod {
    CREDIT_CARD = 'CREDIT_CARD',
    DEBIT_CARD = 'DEBIT_CARD',
    PAYPAL = 'PAYPAL'
}

export interface PaymentDetails {
    amount: number;
    currency: string;
    method: PaymentMethod;
    customerId: string;
    orderId: string;
}

export class PaymentProcessor {
    constructor(private apiKey: string) {}

    async processPayment(details: PaymentDetails): Promise<any> {
        this.validatePaymentDetails(details);
        const fee = this.calculateFee(details.amount, details.method);
        
        return {
            transactionId: this.generateTransactionId(),
            status: PaymentStatus.COMPLETED,
            amount: details.amount,
            fee,
            processedAt: new Date()
        };
    }

    private validatePaymentDetails(details: PaymentDetails): void {
        if (!details.amount || details.amount <= 0) {
            throw new Error('El monto debe ser mayor que 0');
        }
        if (!details.currency || details.currency.length !== 3) {
            throw new Error('Código de moneda inválido');
        }
    }

    private calculateFee(amount: number, method: PaymentMethod): number {
        const rates = {
            CREDIT_CARD: 0.029,
            DEBIT_CARD: 0.019,
            PAYPAL: 0.034
        };
        return Math.round(amount * rates[method] * 100) / 100;
    }

    private generateTransactionId(): string {
        return 'TXN_' + Date.now();
    }
}
```

### 🎯 Tu Misión

Crear tests que cubran:
1. ✅ Validaciones de entrada
2. ✅ Cálculo de fees
3. ✅ Casos edge
4. ✅ Manejo de errores

### 💡 Pistas para usar Copilot

```typescript
import { PaymentProcessor, PaymentMethod } from './payment-processor';

describe('PaymentProcessor', () => {
    let processor: PaymentProcessor;
    
beforeEach(() => {
        processor = new PaymentProcessor('test-key');
    });
    
it('debe procesar pago válido', async () => {
        // Copilot completará
    });
});
```

### ✅ Criterios de Éxito

- [ ] Cobertura > 90%
- [ ] Tests para todos los métodos de pago
- [ ] Tests para validaciones
- [ ] Tests independientes
- [ ] Nombres descriptivos

---

## 📊 Reflexión

### Preguntas
1. ¿Cuánto tiempo ahorró la IA?
2. ¿Qué casos edge sugirió la IA?
3. ¿Los tests son mantenibles?

### Mejores Prácticas
- ✅ Guiar a Copilot con comentarios
- ✅ Revisar tests generados
- ✅ Usar nombres descriptivos

---

[⬅️ Volver](./README.md) | [Siguiente →](./ejercicio-1.6-migracion-lenguaje.md)