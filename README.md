# Agentic RAG Chatbot Prototype

## A projekt célja
Ez a repository egy Agentic Retrieval-Augmented Generation (RAG) alapú chatbot működőképes prototípusát tartalmazza. A megoldás demonstrálja az autonóm döntéshozatalt és a részfeladatok végrehajtását a LangGraph keretrendszer segítségével.

## Architektúra és Döntéshozatal (Design Decisions)
A feladatkiírásnak megfelelően a projekt nem használ fizetős API-kat. A tervezés során az alábbi opciókat vizsgáltam meg:
1. **Lokális nyílt forráskódú modellek (pl. Ollama/Llama3):** A prototípus hardverfüggetlen skálázhatósága és a gyorsabb fejlesztési iterációk miatt elvetve.
2. **HuggingFace Free Inference API:** A gyakori "rate limit" korlátozások és az instabilitás miatt elvetve.
3. **Google Gemini API (Free Tier):** Ez a megoldás lett kiválasztva. Maradéktalanul teljesíti a "nem fizetős" kritériumot (Google AI Studio Free Tier), ugyanakkor biztosítja azt a megbízhatóságot, sebességet és intelligenciát, ami egy Agentic LangGraph rendszer stabil működéséhez és a döntési útvonalak (routing) hibátlan futásához szükséges. A LangChain implementációnak köszönhetően a modell a későbbiekben egyetlen kódsor módosításával cserélhető bármilyen más nyílt vagy zárt modellre.

## Telepítés és Futtatás

1. **Virtuális környezet létrehozása és aktiválása:**
   ```bash
   python -m venv venv
   # Windows:
   venv\Scripts\activate
   # Linux/Mac:
   source venv/bin/activate