Modelos de Lenguaje Grande (LLMs) – Estado del Arte
Este seminario-taller aborda los LLMs desde los fundamentos teóricos hasta aplicaciones y aspectos éticos actuales. A continuación se resumen los avances más recientes en cada tema clave del curso, citando artículos de 2022–2025 relevantes.
Fase 1: Fundamentos históricos y estado del arte en LLMs
Los modelos de lenguaje han evolucionado desde enfoques de n-gramas y LSTM/RNN hasta arquitecturas basadas en Transformers. El hito clave fue Vaswani et al. (2017) con “Attention Is All You Need”, que introdujo el Transformer basado únicamente en auto-atención y superó a los modelos basados en RNN/CNN en traducción automática
arxiv.org
. A modo de ilustración, la Figura a continuación muestra la arquitectura general de un Transformer (módulos de codificador-decodificador, con capas de auto-atención y feedforward): Figura: Esquema de la arquitectura Transformer (codificadores y decodificadores con atención multi-cabeza). Desde entonces, los PLMs preentrenados a gran escala han demostrado “capacidades emergentes” al aumentar su tamaño. Un estudio reciente de Zhao et al. (2023) muestra que al escalar el modelo más allá de cierto umbral, surgen nuevas habilidades (razonamiento, in-context learning) propias de los LLMs
arxiv.org
. Por ejemplo, los modelos a gran escala han permitido a ChatGPT (OpenAI) generar texto humanoide en conversacional (pocos ejemplos) y superar barreras en tareas lingüísticas. En resumen, los Transformers preentrenados (PLMs) de gran tamaño constituyen el estado del arte actual, favoreciendo la paralelización y el aprendizaje no supervisado en vastos corpus
arxiv.org
arxiv.org
.
Fase 1: Modelos fundacionales (BERT, GPT, T5, LLaMA, Falcon, Mistral)
Se estudiarán los papeles fundamentales y las arquitecturas base recientes. Además de los clásicos (BERT, GPT-3, T5), se revisan los últimos modelos de acceso abierto:
BERT (Devlin et al., 2019): pre-entrena un Transformer bidireccional en texto masivo y se afina para tareas de comprensión. Devlin et al. demuestran que con un simple ajuste de capa de salida se obtienen resultados SOTA en múltiples benchmarks (GLUE, SQuAD, etc.)
arxiv.org
.
GPT-3 (Brown et al., 2020): modelo autoregresivo de 175 mil millones de parámetros. Brown et al. muestran que, sin ajustes adicionales, GPT-3 alcanza rendimiento competitivo en tareas de traducción, QA y razonamiento usando solo ejemplos en contexto (few-shot)
arxiv.org
.
T5 (Raffel et al., 2020): unifica todas las tareas de NLP como problemas texto a texto. Raffel et al. entrenan T5 con un gran corpus (Colossal Clean Crawled Corpus) y logran SOTA en resumen, QA y clasificación, demostrando la eficacia del preentrenamiento a gran escala
arxiv.org
.
LLaMA (Touvron et al., 2023): meta introduce una serie de modelos abiertos de 7B a 65B parámetros, entrenados en datos públicos. LLaMA-13B supera a GPT-3 (175B) en la mayoría de benchmarks, y LLaMA-65B es competitivo con Chinchilla-70B y PaLM-540B
arxiv.org
. Su código y pesos se liberan bajo licencia Apache 2.0, impulsando la investigación abierta.
Falcon (Launay et al., 2023): TII publica modelos de 7B, 40B y 180B. El más grande (180B) se entrenó en 3.5 billones de tokens y ”supera significativamente” a otros LLMs (PaLM, Chinchilla) y rivaliza con GPT-4 o PaLM-2-Large, con menor costo de entrenamiento
arxiv.org
. Falcons son de acceso abierto.
Mistral 7B (Jiang et al., 2023): modelo de 7B parámetros optimizado para rendimiento y eficiencia. Integra Grouped-Query Attention y sliding-window attention, y logra superar a LLaMA-2 13B en benchmarks de razonamiento, matemáticas y código
arxiv.org
. También se ofrece una versión afinada en instrucciones bajo licencia Apache 2.0.
En conjunto, estos modelos fundacionales demuestran que el ecosistema de LLMs abiertos ha avanzado rápidamente en 2022–2024. Por ejemplo, modelos de ~7B–13B (Mistral, LLaMA-7B) pueden igualar o superar a modelos anteriores mucho mayores, gracias a mejoras arquitectónicas y de entrenamiento
arxiv.org
arxiv.org
.
Fase 2: Preprocesamiento y fine-tuning eficiente
Tokenización: los LLMs modernos suelen usar subword tokenization. Por ejemplo, el algoritmo de Byte-Pair Encoding (BPE) introducido por Sennrich et al. (2016) segmenta palabras raras en subunidades aprendidas, mejorando la cobertura de vocabulario
arxiv.org
. Otros métodos comunes son WordPiece y SentencePiece, que abordan el problema de vocabulario abierto al generar fragmentos de palabras.
Ajuste fino eficiente: técnicas recientes buscan reducir parámetros entrenables durante el fine-tuning:
LoRA (Hu et al., 2021): congela el modelo base y añade matrices de baja dimensión entrenables. LoRA logra adaptar modelos gigantescos con ~10 000× menos parámetros libres
arxiv.org
, facilitando versiones específicas sin copiar todo el modelo.
QLoRA (Dettmers et al., 2023): extiende LoRA al uso de 4-bit quantización en entrenamiento. Esto permite afinar modelos de hasta 65B en GPUs de 48GB, manteniendo rendimiento completo (chat según GPT-3)
arxiv.org
.
Prompt-tuning / Prefix-tuning: en lugar de ajustar pesos, se optimiza un pequeño vector continuo (“prefijo”) que alimenta al modelo. Li & Liang (2021) muestran que aprender solo 0.1% de los parámetros en el prefijo iguala el rendimiento de fine-tuning completo en datos amplios
aclanthology.org
.
Adapters (Houlsby et al., 2019): módulos adicionales insertados entre capas. Los adapters añaden pocos parámetros por tarea (~3.6%) y alcanzan resultados casi SOTA con arquitectura base fija
arxiv.org
.
Estas técnicas (LoRA, QLoRA, prompt-tuning, adapters) permiten experimentar con distintas arquitecturas de LLMs de forma práctica, sin costear el ajuste completo. En la Fase 2 del proyecto, se instalan pipelines de fine-tuning con Hugging Face Transformers, empleando LoRA/QLoRA (y eventualmente técnicas como prompt tuning y adapters), comparando resultados y parámetros entrenados
arxiv.org
arxiv.org
aclanthology.org
arxiv.org
.
Fase 3: Evaluación, interpretabilidad y fairness
Métricas de evaluación: se utilizan métricas automatizadas como perplejidad (para modelos de lenguaje), BLEU/ROUGE (para traducción/resumen) y F1/precisión/Exactitud (para clasificación). Estudios recientes señalan que el uso de métricas automáticas ha crecido en NLP
arxiv.org
, pero a menudo se combinan con evaluaciones humanas o análisis cualitativos. En el proyecto, se aplicarán estas métricas para comparar modelos ajustados, así como análisis de errores en muestras.
Interpretabilidad: visualizaciones de atención ofrecen intuición sobre las “decisiones” del modelo. Por ejemplo, es común graficar mapas de atención entre palabras para ver qué tokens influyen en la predicción
arxiv.org
. Aunque la correlación de atención con importancias reales es debatida, las visualizaciones de atención (o de gradientes y saliencias) ayudan a diagnosticar comportamientos del modelo. Herramientas como captum (PyTorch) o Transformer Explainability facilitan este análisis.
Fairness y ética: los LLMs pueden reflejar y amplificar sesgos sociales presentes en sus datos de entrenamiento. La revisión de Gallegos et al. (2023) ofrece un panorama exhaustivo: los LLMs “pueden aprender, perpetuar y amplificar sesgos sociales dañinos”
arxiv.org
, por lo que se han desarrollado métricas (p. ej. tests contrafactuales) y métodos de mitigación (preprocesamiento, ajuste intra/post entrenamiento) para intentar controlarlos. Además, se discute el fenómeno de alucinaciones: los LLMs a veces generan contenido plausible pero falso. Huang et al. (2024) catalogan las causas y propuestas anti-alucinación en LLMs, pues esto afecta la confiabilidad de aplicaciones RAG
arxiv.org
. En el proyecto, se evaluarán cuantitativa y cualitativamente sesgos o errores del modelo (p. ej. generación inventada, sesgo de género/raza, robustez al cambio de dominio) y se comparará con literatura relevante.
Fase 4: Deployment, optimización y aplicaciones avanzadas
Despliegue de modelos: se construyen APIs o demos con frameworks como FastAPI, Flask o apps interactivas con Streamlit/Gradio. Estos ambientes permiten exponer el modelo entrenado (chatbot, servicio de clasificación, etc.) para usuarios finales o pruebas de carga.
Optimización y compresión: para producción, a menudo se usan técnicas de quantización y pruning. Por ejemplo, convertir pesos de 32-bit a 8-bit puede reducir el tamaño del modelo ~4× sin gran pérdida
arxiv.org
. Un estudio reciente repasa estas técnicas: el pruning elimina parámetros redundantes (capas o cabezas de atención) y la quantización baja la precisión numérica, ahorrando memoria y velocidad
arxiv.org
. También se considera distilación de conocimiento para crear modelos más pequeños. En el proyecto se explorarán al menos la quantización post-training (p. ej. librería bitsandbytes) y, si es viable, el pruning de cabezas de atención.
Aplicaciones avanzadas: además de chatbots y clasificación, se implementarán casos de uso como RAG (Retrieval-Augmented Generation) y sistemas de agentes. RAG (Lewis et al., 2020) combina un LLM con un buscador de información (por ejemplo Wikipedia): durante la generación se recuperan pasajes relevantes que luego se integran al contexto, mejorando la factualidad del texto generado
arxiv.org
. Este enfoque permite aplicaciones de QA “abierto” con conocimiento actualizado. Por otro lado, los agentes basados en LLMs (usando frameworks tipo LangChain o AutoGPT) extienden el modelo con capacidades de planificar tareas, usar herramientas externas y memoria, que son tendencia actual en 2024.
Consideraciones éticas y sostenibilidad: se reflexionará sobre el costo energético y la huella de carbono del entrenamiento (por ejemplo, GPT-3 requiere ~350 GB de almacenamiento en GPU y genera un alto consumo energético
arxiv.org
). Se discutirán pautas de uso responsable (p. ej. monitorear alucinaciones, respetar la privacidad de datos de entrenamiento). En la documentación final se incluirá una sección de “reflexión ética” comparando con literatura relevante (por ejemplo, Stochastic Parrots de Bender et al. o guías de IA responsable).
Recursos y bibliografía adicional reciente (2022–2025)
Además de la bibliografía fundamental ya listada (Vaswani 2017, Devlin 2019, Brown 2020, Raffel 2020, Touvron 2023, etc.), se incorporarán artículos recientes para cada tema:
A Survey of Large Language Models (Zhao et al., 2023) proporciona un panorama general de LLMs modernos, sus capacidades emergentes y desafíos
arxiv.org
.
Bias and Fairness in LLMs (Gallegos et al., 2023) encuadra métodos de evaluación y mitigación de sesgos
arxiv.org
.
Hallucination Survey in LLMs (Huang et al., 2024) detalla el problema de generación de contenido no factual
arxiv.org
.
QLoRA (Dettmers et al., 2023) y LoRA (Hu et al., 2021) son lecturas imprescindibles sobre ajustes eficientes
arxiv.org
arxiv.org
.
Prefixes, Adapters (Li et al., 2021; Houlsby et al., 2019) para entender técnicas de fine-tuning ligero
aclanthology.org
arxiv.org
.
Mistral 7B (Jiang et al., 2023) y Falcon Models (Almazrouei et al., 2023) explican los últimos LLMs abiertos de alto desempeño
arxiv.org
arxiv.org
.
Transformer Compression Survey (Tang et al., 2024) revisa técnicas de quantización, pruning y distilación aplicadas a LLMs
arxiv.org
.
Documentación técnica de Hugging Face Transformers, PaperswithCode y repositorios de código reciente servirán de guía práctica.
En conclusión, este temario requiere integrar lecturas clásicas con papers de vanguardia (2022–2025) sobre modelos LLM, sus adaptaciones eficientes y consideraciones de evaluación, interpretabilidad y ética. Cada fase del proyecto combinará teoría (artículos científicos) con práctica (implementación de modelos ajustados y evaluados), promoviendo una comprensión profunda del estado actual de los LLMs. Cada afirmación clave del seminario estará respaldada por las citas señaladas arriba, asegurando rigor científico en la documentación final. Fuentes principales: Artículos científicos referenciados en cada sección (enlaces citados)
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
aclanthology.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
arxiv.org
. (Se omiten aquí por brevedad referencias clásicas listadas en la bibliografía del curso.)
Citations

[1706.03762] Attention Is All You Need

https://arxiv.org/abs/1706.03762

[2303.18223] A Survey of Large Language Models

https://arxiv.org/abs/2303.18223

[1810.04805] BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

https://arxiv.org/abs/1810.04805

[2005.14165] Language Models are Few-Shot Learners

https://arxiv.org/abs/2005.14165

[1910.10683] Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer

https://arxiv.org/abs/1910.10683

[2302.13971] LLaMA: Open and Efficient Foundation Language Models

https://arxiv.org/abs/2302.13971

[2311.16867] The Falcon Series of Open Language Models

https://arxiv.org/abs/2311.16867

[2310.06825] Mistral 7B

https://arxiv.org/abs/2310.06825

[1508.07909] Neural Machine Translation of Rare Words with Subword Units

https://arxiv.org/abs/1508.07909

[2106.09685] LoRA: Low-Rank Adaptation of Large Language Models

https://arxiv.org/abs/2106.09685

https://arxiv.org/pdf/2305.14314

Prefix-Tuning: Optimizing Continuous Prompts for Generation - ACL Anthology

https://aclanthology.org/2021.acl-long.353/

[1902.00751] Parameter-Efficient Transfer Learning for NLP

https://arxiv.org/abs/1902.00751

Automatic Metrics in Natural Language Generation: A Survey of Current Evaluation Practices

https://arxiv.org/html/2408.09169v1

https://arxiv.org/pdf/2309.01029

[2309.00770] Bias and Fairness in Large Language Models: A Survey

https://arxiv.org/abs/2309.00770

[2311.05232] A Survey on Hallucination in Large Language Models: Principles, Taxonomy, Challenges, and Open Questions

https://arxiv.org/abs/2311.05232

A Survey on Transformer Compression

https://arxiv.org/html/2402.05964v2

[2005.11401] Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks

https://arxiv.org/abs/2005.11401

A Survey on Transformer Compression

https://arxiv.org/html/2402.05964v2