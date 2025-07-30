
# 🎯 AI-Based Time Slot Prediction Model – Smart India Hackathon 2024

Welcome to our AI-powered solution developed for **Smart India Hackathon 2024**, aimed at solving one of the real-world problem statements using predictive intelligence.

This project leverages historical data and advanced machine learning techniques to **predict optimal time slots** for processes, appointments, or sessions – ensuring efficiency, reduced wait times, and smart decision-making.

---

## 🚀 What this project solves

- Manual scheduling is inefficient.
- Peak hours create congestion.
- Lack of data-driven decisions leads to poor resource use.

Our model fixes this by predicting time slots using intelligent data analysis and forecasting techniques, which can easily be integrated into real-world appointment systems.

---

## 🧩 Key Features

- 📊 Predicts time slots based on historical usage.
- 🤖 AI model trained on real data.
- 💡 Fast API for predictions.
- 🧠 Supports scalability for large datasets.
- ⚙️ Easily customizable and deployable.

---

## ⚙️ Tech Stack

- **Python** for ML model development
- **Pandas, NumPy, Scikit-learn** for data processing and ML
- **FastAPI** for API endpoints
- **Git + GitHub** for version control
- **Jupyter Notebook** for model experimentation

---

## 🧠 Architecture

+---------------------------------------------------------------------------------+
|                         SYSTEM ARCHITECTURE & DATA FLOW                         |
+---------------------------------------------------------------------------------+

                                    [START]
                                       |
                                       V
                          +-------------------------+
                          |  User-Facing Web Portal |
                          +-------------------------+
                                       |
                   +-------------------+-------------------+
                   |                                       |
    // --- SENDER's JOURNEY ---                        // --- RECIPIENT's JOURNEY ---
                   |                                       |
                   V                                       V
      +----------------------------+          +-----------------------------+
      | 1. Sender Enters Ref. No.  |          | 1a. Recipient Enters Ref. No|
      +----------------------------+          +-----------------------------+
                   |                                       |
                   V                                       V
      +----------------------------+          +-----------------------------+
      | 2. AI Model Predicts Time  |          | 2a. Track & View Time       |
      +----------------------------+          +-----------------------------+
                   |                                       |
                   V                                       V
      <   3. Sender Satisfied?   >          <   3a. Recipient Satisfied?  >
            |              |                      |               |
       YES  |              |  NO             YES  |               |  NO
            |              |                      |               |
            |       +---------------------+       |        +----------------------+
            |       | Proposes New Time   |       |        | Proposes New Time    |
            |       +---------------------+       |        +----------------------+
            |              |                      |               |
            |              V                      |               V
            |       < AI Re-evaluates >           |        < AI Re-evaluates >
            |              |                      |               |
            +--------------+----------------------)---------------+--------------+
                                       |
                                       V
                  +-----------------------------------------+
                  |  4. SCHEDULING & BACKEND CONFIRMATION   |
                  +-----------------------------------------+
                                       |
      <<============== Writes & Reads =============>>
    +-----------------------------------------------------+
    |                  D A T A B A S E                    |
    | (User Info, Historical Success Rates, Preferences)  |
    +-----------------------------------------------------+
      <<===============================================>>
                                       |
                                       V
                     // --- PORTAL OFFICE's WORKFLOW ---

                  +-----------------------------------------+
                  |  5. View Confirmed Schedule on Dashboard|
                  +-----------------------------------------+
                                       |
                                       V
+---------------------------------------------------------------------------------+
|         6. OPTIMIZE ROUTE (optimize_route.py using Google OR-Tools)             |
+---------------------------------------------------------------------------------+
                                       |
                                       V
                          +-------------------------+
                          |  7. Assign Route to Staff   |
                          +-------------------------+
                                       |
                                       V
                           < Can Delivery Be Made? >
                                 |         |
                            YES  |         | NO
                                 |         |
                                 V         +-----> (Reschedule Within Range)
                     +---------------------+
                     | 8. DELIVERY SUCCESSFUL|
                     +---------------------+
                                 |
                                 V
                     +---------------------+
                     | 9. Collect User Rating|-----> (Update Database w/ New Data)
                     +---------------------+
                                 |
                                 V
                               [STOP]
---

## 🛠️ Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/ashmitasenroy/SIH---AI-based-time-slot-prediction-model.git
cd SIH---AI-based-time-slot-prediction-model
````

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the model / API

* To test the prediction logic:

```bash
python model.py
```

* To run the FastAPI app:

```bash
uvicorn app:app --reload
```

Visit: `http://127.0.0.1:8000/docs` for Swagger UI.

---

## 👩🏻‍💻 Developed By

 **Ritusree Das** 
 **Mohak Das** 
 **Rudranil Choudhary** 
 **Surya Pratap Verma** 
 **Anisha Singh** ([@anisha-singh-2004](https://github.com/anisha-singh-2004))
 **Ashmita Sen Roy** ([@ashmitasenroy](https://github.com/ashmitasenroy))
 

    
  

Thanks to SIH mentors and coordinators for their support!

---

## 📄 License

This project is under the **MIT License**. See the [LICENSE](LICENSE) file for more info.

---

## 💬 Feedback?

Feel free to raise issues or contribute via pull requests.

