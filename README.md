# Agentic RAG Chatbot Prototype

## A projekt célja
Ez a repository egy Agentic Retrieval-Augmented Generation (RAG) alapú chatbot működőképes prototípusát tartalmazza. A megoldás demonstrálja az autonóm döntéshozatalt és a részfeladatok végrehajtását a LangGraph keretrendszer segítségével.

## Architektúra és Döntéshozatal (Design Decisions)
A feladatkiírásnak megfelelően a projekt mentes a fizetős API-któl. A tervezés során iteratív megközelítést alkalmaztam:
1. **Lokális modellek (pl. Ollama):** A hardverfüggőség és a lassú válaszidők miatt elvetve.
2. **Google Gemini API (Free Tier):** A kezdeti prototípus ezt használta, azonban a szigorú rate-limitek (429 Resource Exhausted) instabillá tették a működést.
3. **Hugging Face Inference API (Kiválasztott megoldás):** A stabilitás érdekében a végső architektúra a Hugging Face felhőjében futó nyílt forráskódú **Qwen 2.5 7B** modellt használja. A task-routing hibák kiküszöbölésére a LangChain `ChatHuggingFace` wrapperét alkalmaztam. Ez a megoldás tökéletesen demonstrálja a LangGraph architektúra cserélhetőségét (modularity) és hibatűrését.

## Telepítés és Futtatás

1. **Virtuális környezet létrehozása és aktiválása:**
   ```bash
   python -m venv venv
   # Windows:
   venv\Scripts\activate
   # Linux/Mac:
   source venv/bin/activate