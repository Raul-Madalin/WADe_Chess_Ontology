# ImagineAlpacas - Chess Ontology Application

## **Overview**
This application allows users to explore chess puzzles using RDF data, search and filter puzzles based on piece configurations, and receive recommendations for similar puzzles.

Youtube presentation [here](https://youtu.be/P1RAD74WKlA).

---

## **1. Backend: Flask API (Microservices)**
### **Purpose**
- Handles search, filtering, recommendations, image serving, and initial loading of chess puzzles.
- Connects to GraphDB for RDF-based chess ontology queries.

### **Technology Stack**
- **Flask** (Python) – REST API framework
- **SPARQL** – Query language for RDF data
- **Blueprints** – Flask modularization for microservices

### **Key Services**
| Endpoint | Description |
|----------|------------|
| `/search` | Search chess puzzles by piece names |
| `/filter` | Apply piece-based filtering and call for game-state filtering if applicable |
| `/filter/game-state-rdf` | RDF-based game state classification |
| `/filter/game-state-ml` | ML-based game state classification |
| `/rdf-recommendTations` | Fetches puzzle recommendations generated by RDF queries |
| `/ml-recommendTations` | Fetches puzzle recommendations generated by ML |
| `/images/<filename>` | Serves chess puzzle images |
| `/initial` | Loads initial chess puzzles |

---

## **2. Frontend: React Application**
### **Purpose**
- Provides UI for searching, filtering, and viewing chess puzzles.
- Fetches recommendations and metadata for puzzles.

### **Technology Stack**
- **React** – Frontend framework
- **Material-UI** – UI components
- **Axios** – HTTP requests
- **React Router** – Navigation

### **Key Features**
- **Search Bar** – Users can search for puzzles by entering chess piece names.
- **Filter Panel** – Users can refine puzzles using RDF-based and piece-based filters.
- **Image Gallery** – Displays chess puzzles as images.
- **Recommendations** – Suggests similar puzzles based on RDF analysis.
- **RDF Metadata** – Integrates structured data to classify puzzles.

---

## **3. Database: GraphDB**
### **Purpose**
- Stores chess puzzles as RDF data.
- Supports SPARQL queries for complex chess logic.
- Enables semantic search and filtering.
- Technology Stack
- GraphDB – Ontotext’s RDF database.
- SPARQL – Query language for RDF.
- RDF Schema – Defines chess puzzle structure.
### **Key Concepts**
- Chess pieces ontology includes kings, queens, rooks, bishops, knights, and pawns.
- SPARQL filters allow searching chess puzzles based on piece configurations.
- Game state classification identifies puzzles as "Opening", "Midgame", or "Endgame".

## Project Structure
```plaintext
WADE_IMAGINEALPACAS/
│
├── app/
│   ├── model/
│   │   └── (Contains model files like `chess_phase_model.h5`)
│   ├── recommender/
│   │   └── (Contains recommendation logic and models, e.g., `knn_model.pkl`)
│   ├── training/
│   │   └── (Contains training scripts or resources)
│   ├── trainingv2/
│   │   └── (Contains version 2 of training scripts or resources)
│   ├── utils/
│   │   ├── config.py
│   │   ├── graphdb_utils.py
│   │   ├── setup_rdf.py
│   │   └── __init__.py
│   └── main.py
│
├── chess_microservices/
│   ├── microservices/
│   │   ├── filter_ml_service.py
│   │   ├── filter_rdf_service.py
│   │   ├── filter_service.py
│   │   ├── image_service.py
│   │   ├── initial_load_service.py
│   │   ├── recommendation_ml_service.py
│   │   ├── recommendation_service.py
│   │   └── search_service.py
│   └── utils/
│       ├── config.py
│       ├── graphdb_utils.py
│       ├── setup_rdf.py
│       └── __init__.py
│
├── chess-visualizer/
│   ├── build/
│   │   └── (Contains built frontend files for deployment)
│   ├── node_modules/
│   │   └── (Contains dependencies for React)
│   ├── public/
│   │   └── (Static assets for React app)
│   ├── src/
│   │   ├── components/
│   │   │   ├── FilterPanel.jsx
│   │   │   ├── ImageGallery.jsx
│   │   │   ├── Recommendations.jsx
│   │   │   └── SearchBar.jsx
│   │   ├── App.css
│   │   ├── App.jsx
│   │   ├── App.test.js
│   │   ├── config.js
│   │   ├── index.css
│   │   ├── index.js
│   │   ├── logo.svg
│   │   ├── reportWebVitals.js
│   │   └── setupTests.js
│
├── dataset/
│   ├── test/
│   │   └── (Contains test images or data)
│   └── train/
│       └── (Contains training images or data)
│
├── .gitignore
├── chess-shapes.ttl
├── ontology.rdf
├── package.json
├── package-lock.json
├── README.md
├── requirements.txt
└── gateway.py
```
