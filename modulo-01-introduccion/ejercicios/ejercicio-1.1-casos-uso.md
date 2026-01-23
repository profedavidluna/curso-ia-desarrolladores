# 📝 Ejercicio 1.1: Identificación de Casos de Uso de IA

**Duración**: 45 minutos  
**Dificultad**: Básica  
**Modalidad**: Individual o en grupos de 2-3 personas

## 🎯 Objetivos

- Analizar tu flujo de trabajo actual como desarrollador
- Identificar oportunidades para aplicar IA en tu día a día
- Priorizar casos de uso según impacto y viabilidad
- Crear un plan de adopción de herramientas de IA

## 📋 Instrucciones

### Parte 1: Análisis de tu Flujo de Trabajo (15 minutos)

Documenta tu flujo de trabajo típico durante una semana de desarrollo:

1. **Planificación**  
   - ¿Cómo defines tareas?  
   - ¿Cómo estimas tiempo?  
   - ¿Qué herramientas usas?

2. **Codificación**  
   - ¿Qué porcentaje de tu tiempo escribes código nuevo?  
   - ¿Cuánto tiempo dedicas a refactorizar?  
   - ¿Qué tipo de código escribes más frecuentemente?

3. **Testing**  
   - ¿Escribes tests unitarios?  
   - ¿Cuánto tiempo dedicas a testing?  
   - ¿Qué tipo de tests realizas?

4. **Debugging**  
   - ¿Cuánto tiempo pasas debuggeando?  
   - ¿Qué tipos de bugs son más comunes?  
   - ¿Cómo resuelves bugs complejos?

5. **Documentación**  
   - ¿Documentas tu código?  
   - ¿Cuánto tiempo dedicas a documentación?  
   - ¿Qué tipo de documentación generas?

6. **Code Review**  
   - ¿Participas en code reviews?  
   - ¿Cuánto tiempo dedicas?  
   - ¿Qué aspectos revisas?

### Parte 2: Identificación de Oportunidades (15 minutos)

Para cada fase de tu flujo de trabajo, identifica:

**Plantilla de Análisis:**

```
Fase: [Nombre de la fase]
Tiempo dedicado: [X horas/semana]
Tareas repetitivas: [Lista de tareas]
Puntos de dolor: [Problemas específicos]
Oportunidad de IA: [Cómo la IA podría ayudar]
Impacto estimado: [Alto/Medio/Bajo]
```

**Ejemplo:**

```
Fase: Debugging
Tiempo dedicado: 8 horas/semana
Tareas repetitivas: 
- Buscar documentación de APIs
- Identificar causa de errores en logs
- Buscar ejemplos de código similar
Puntos de dolor:
- Errores de concurrencia difíciles de reproducir
- Stack traces largos y confusos
Oportunidad de IA:
- Usar ChatGPT para explicar stack traces
- Copilot para sugerir fixes comunes
- IA para analizar patrones en logs
Impacto estimado: Alto
```

### Parte 3: Priorización de Casos de Uso (15 minutos)

Usa esta matriz para priorizar:

| Caso de Uso | Impacto | Esfuerzo | Prioridad | Herramienta |
|-------------|---------|----------|-----------|-------------|
| Autocompletado de código | Alto | Bajo | 🔴 Alta | GitHub Copilot |
| Generación de tests | Alto | Bajo | 🔴 Alta | Copilot |
| Explicación de código legacy | Medio | Bajo | 🟡 Media | ChatGPT |
| ... | ... | ... | ... | ... |

**Leyenda:**  
- 🔴 **Alta**: Implementar en las próximas 2 semanas  
- 🟡 **Media**: Implementar en 1-2 meses  
- 🟢 **Baja**: Evaluar en el futuro

## ✅ Entregable

Crea un documento con:

1. **Análisis de Flujo de Trabajo** (diagrama o tabla)
2. **Lista de Oportunidades** (mínimo 5)
3. **Matriz de Priorización** (mínimo 5 casos de uso)
4. **Plan de Acción** (3 casos de uso prioritarios con timeline)

## 💡 Ejemplo de Plan de Acción

```markdown
# Plan de Adopción de IA - [Tu Nombre]

## Caso de Uso 1: Autocompletado de Código con GitHub Copilot
- **Timeline**: Semana 1-2
- **Acción**: Instalar Copilot y usarlo en proyecto actual
- **Métrica**: Medir tiempo de desarrollo antes/después
- **Objetivo**: Reducir 20% tiempo de codificación

## Caso de Uso 2: Generación Automática de Tests
- **Timeline**: Semana 3-4
- **Acción**: Usar Copilot para generar tests unitarios
- **Métrica**: Cobertura de tests
- **Objetivo**: Alcanzar 80% de cobertura

## Caso de Uso 3: Code Review Asistido
- **Timeline**: Mes 2
- **Acción**: Usar ChatGPT para revisar PRs
- **Métrica**: Tiempo de code review
- **Objetivo**: Reducir 30% tiempo de review
```

## 🤔 Preguntas de Reflexión

1. ¿Qué tarea consume más tiempo en tu día a día?
2. ¿Dónde sientes más "fricción" en tu flujo de trabajo?
3. ¿Qué tareas te resultan más repetitivas?
4. ¿Qué te gustaría automatizar con IA?

## 📚 Recursos Adicionales

- [GitHub Copilot Use Cases](https://github.com/features/copilot)
- [AI for Developers Survey 2024](https://stackoverflow.blog/2024/ai-developers/)
- [Developer Productivity Metrics](https://queue.acm.org/detail.cfm?id=3454124)

---

[⬅️ Volver al Módulo 1](../README.md) | [Siguiente: Exploración de Herramientas →](./ejercicio-1.2-exploracion-herramientas.md)