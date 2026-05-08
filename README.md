a# 🔗 Blockchain-Based Event Detection & Trust Verification Using NLP & ML

A full-stack intelligent system that detects and classifies real-world events from unstructured text (tweets/news), verifies their trustworthiness using Machine Learning, and stores validated events on the **Ethereum blockchain** for tamper-proof, permanent record keeping.

---

## 📌 Problem Statement

In the age of social media, misinformation spreads faster than facts. Detecting whether a reported event is **real or misleading** — and storing verified events in a way that cannot be altered — is a critical challenge.

This project solves it by combining:
- **NLP + ML** to classify events from raw text
- **Blockchain (Ethereum)** to store verified events permanently and transparently

---

## 🎯 Key Results

| Metric | Result |
|---|---|
| Classification Accuracy | **85–90%** on test data |
| Dataset | Disaster Tweets (real-world Twitter data) |
| Blockchain Storage | Tamper-proof via Ethereum smart contract |
| Web Interface | Full Django web app with login, predict, visualize |

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.7 | Core language |
| Django | Web framework & backend |
| NLP (TF-IDF) | Text feature extraction |
| Deep Learning (Keras/TensorFlow) | Event classification model |
| Solidity (Ethereum) | Smart contract for blockchain storage |
| hello-eth | Local Ethereum blockchain server |
| Node.js v12 | Required for hello-eth blockchain tool |
| SQLite | Local database |
| HTML / CSS | Frontend templates |

---

## 📁 Project Structure

```
Blockchain/
│
├── BlockchainEventDetection/        # Django project root
│   ├── Dataset/
│   │   ├── DisasterTweets.csv       # Training dataset
│   │   └── testTweet.csv            # Test dataset
│   ├── Event/                       # Django settings & config
│   │   ├── settings.py
│   │   └── urls.py
│   ├── EventApp/                    # Main application
│   │   ├── views.py                 # Core ML logic & blockchain integration
│   │   ├── models.py                # Database models
│   │   ├── templates/               # HTML pages
│   │   │   ├── index.html
│   │   │   ├── Predict.html         # Event prediction page
│   │   │   ├── Register.html
│   │   │   ├── UserLogin.html
│   │   │   ├── ViewGraph.html       # Result visualizations
│   │   │   └── ViewOutput.html
│   │   └── static/                  # CSS & images
│   ├── model/                       # Trained ML model files
│   │   ├── dl_weights.hdf5
│   │   ├── X.npy
│   │   └── Y.npy
│   └── run.bat                      # One-click app launcher
│
├── Event.sol                        # Ethereum smart contract (Solidity)
└── hello-eth/                       # Local Ethereum blockchain server
```

---

## ⚙️ How It Works

1. **User Registration & Login** — Secure user authentication via Django
2. **Text Input** — User submits a tweet or news snippet through the web interface
3. **NLP Preprocessing** — Text is cleaned, tokenised, and converted to TF-IDF features
4. **ML Classification** — Deep learning model predicts whether the event is real or misleading (85–90% accuracy)
5. **Blockchain Storage** — Verified user and event data is stored via the `Event.sol` Ethereum smart contract using `addUser()` and `setPost()` functions — making records permanent and tamper-proof
6. **Visualisation** — Results and accuracy graphs are displayed on the dashboard

---

## 🚀 How to Run

### Prerequisites
- **Python 3.7.0** (exact version required)
- **Node.js v12.13.1** (required for hello-eth blockchain server)

---

### Step 1 — Install Python dependencies
```bash
cd BlockchainEventDetection
pip install -r requirements.txt
```

---

### Step 2 — Start the Ethereum blockchain server
```bash
cd hello-eth
# Follow the screenshots in SCREENS folder to start the local blockchain server
# After contract deployment, copy the contract address shown under the EVENT section
```

---

### Step 3 — Update the contract address
After deploying the smart contract, copy the new contract address and replace it in:
```
BlockchainEventDetection/EventApp/views.py
```
Look for this line at **line 202 and line 222:**
```python
'0xd374Cb05bd6187D6cF905D7bBD85f2b704fBDD29'
```
Replace with your newly deployed contract address.

---

### Step 4 — Start the Django application
```bash
cd BlockchainEventDetection
# Double-click run.bat  (Windows)
# OR run manually:
python manage.py runserver
```

### Step 5 — Open in browser
```
http://127.0.0.1:8000
```

---

## ⛓️ Smart Contract — Event.sol

```solidity
contract Event {
    // Stores user details on blockchain
    function addUser(string memory us) public { ... }
    function getUser() public view returns (string memory) { ... }

    // Stores verified event/post data on blockchain
    function setPost(string memory p) public { ... }
    function getPost() public view returns (string memory) { ... }
}
```

Every verified event is written to the Ethereum blockchain — **immutable, transparent, and permanently verifiable.**

---

## 🧠 ML Model Details

- **Dataset:** Disaster Tweets — real-world Twitter data labelled as real or misleading
- **Feature Extraction:** TF-IDF vectorisation on preprocessed text
- **Model:** Deep learning classifier (weights: `dl_weights.hdf5`)
- **Accuracy:** 85–90% on test data

---

## 📦 Requirements

```
django
scikit-learn
numpy
pandas
tensorflow
keras
web3
```

---

## 🔮 Future Improvements

- [ ] Deploy smart contract on public Ethereum testnet (Sepolia)
- [ ] Integrate live Twitter/X API for real-time detection
- [ ] Upgrade to BERT-based NLP model for higher accuracy
- [ ] Public dashboard for verified event tracking

---

## 👩‍💻 Author

**Sandhya Ravula**
- GitHub: [@Ravula-sandhya](https://github.com/Ravula-sandhya)
- LinkedIn: [linkedin.com/in/sandhya-ravula](https://linkedin.com/in/sandhya-ravula)
- Email: ravulasandhya45@gmail.com

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
