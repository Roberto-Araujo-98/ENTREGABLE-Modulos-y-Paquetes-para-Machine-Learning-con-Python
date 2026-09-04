graph TD
    %% Definición de paleta de colores moderna
    classDef datos fill:#FFE0B2,stroke:#F57C00,stroke-width:2px,color:#E65100,font-weight:bold
    classDef preproc fill:#E1BEE7,stroke:#8E24AA,stroke-width:2px,color:#4A148C,font-weight:bold
    classDef modelos fill:#C8E6C9,stroke:#388E3C,stroke-width:2px,color:#1B5E20,font-weight:bold
    classDef metricas fill:#BBDEFB,stroke:#1976D2,stroke-width:2px,color:#0D47A1,font-weight:bold

    subgraph INGESTA [1. Origen de Datos]
        A[(opiniones.csv)]:::datos
        B[(mercado.csv)]:::datos
    end

    subgraph PROCESAMIENTO [2. Transformación y NLP]
        C{{Limpieza texto con spaCy}}:::preproc
        D{{Vectorización TF-IDF}}:::preproc
        E{{Escalado StandardScaler}}:::preproc
    end

    subgraph IA [3. Modelos Predictivos]
        F((Clasificador Logístico)):::modelos
        G((Pipeline RoBERTuito)):::modelos
        H((Red Neuronal Keras)):::modelos
    end

    subgraph SALIDA [4. Resultados y Visualización]
        I[/Matriz de Confusión/]:::metricas
        J[/Gráfico de Tendencias/]:::metricas
    end

    %% Conexiones principales
    A --> C
    C --> D
    D --> F
    D --> G

    B --> E
    E --> H

    F --> I
    G --> I
    H --> J
