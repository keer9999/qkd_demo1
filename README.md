# BB84 Quantum Key Distribution Simulator

An interactive web-based simulator for the BB84 quantum key distribution protocol, built with Streamlit and deployed using stlite on GitHub Pages.

## 🚀 Live Demo

Once deployed, your app will be available at: `https://keer9999.github.io/qkd_demo1/`

## ✨ Key Feature: Pure Python Implementation

This simulator uses a **pure Python quantum simulation** approach instead of Qiskit, making it:
- ✅ **Browser-compatible** - Runs perfectly on GitHub Pages
- ✅ **Fast loading** - Only requires numpy, pandas, matplotlib
- ✅ **Educationally equivalent** - Same BB84 behavior and results
- ✅ **No compilation** - No C++ extensions needed

## 📋 Features

- **Interactive Simulation**: Configure parameters and run BB84 protocol simulations in real-time
- **Visual Timeline**: Detailed visualization of bit transmission, basis matching, and errors
- **Scenario Comparison**: Compare secure transmission (no eavesdropper) vs. compromised transmission (with Eve)
- **Educational**: Learn about quantum cryptography with built-in explanations
- **No Server Required**: Runs entirely in your browser using WebAssembly (Pyodide)
- **Pure Python**: No heavy quantum libraries - perfect for web deployment

## 🛠️ Technology Stack

- **Streamlit**: Web application framework
- **stlite**: Serverless Streamlit using WebAssembly
- **Pure Python Quantum Simulator**: Custom BB84 implementation
- **NumPy & Pandas**: Data processing
- **Matplotlib**: Visualization
- **GitHub Pages**: Free static hosting

## 🔬 How It Works

The simulator implements BB84 quantum behavior using pure Python:

```python
@staticmethod
def measure_qubit(bit, send_basis, measure_basis):
    # If bases match: measurement is deterministic
    if send_basis == measure_basis:
        return bit
    # If bases don't match: random result (quantum uncertainty)
    return np.random.randint(0, 2)
```

This correctly models:
- ✅ Basis matching → deterministic measurement (bit preserved)
- ✅ Basis mismatch → random 50/50 outcome (quantum collapse)
- ✅ Eavesdropping → detectable errors in transmission
- ✅ QBER calculation → same as full quantum simulation

## 📦 Deployment Instructions

### Step 1: Create a GitHub Repository

1. Go to [GitHub](https://github.com) and create a new repository
2. Name it something like `bb84-simulator`
3. Make it **public** (required for GitHub Pages)
4. Don't initialize with README (we'll add files)

### Step 2: Upload Files

**Option A: Web Interface (Easiest)**

1. Go to your new repository
2. Click "Add file" → "Upload files"
3. Drag and drop `index.html`
4. Commit with message: "Deploy BB84 simulator"

**Option B: Command Line**

```bash
git clone https://github.com/keer9999/qkd_demo1.git
cd qkd_demo1

# Copy index.html to this folder
git add index.html
git commit -m "Deploy BB84 simulator"
git push origin main
```

### Step 3: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** (top navigation)
3. Click **Pages** (left sidebar)
4. Under "Source", select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**
6. Wait 2-3 minutes for deployment
7. Your app will be live at: `https://keer9999.github.io/qkd_demo1/`

### Step 4: Verify Deployment

1. Wait 2-3 minutes after enabling Pages
2. Visit your GitHub Pages URL
3. You should see the BB84 simulator loading
4. Initial load takes 5-15 seconds (downloading packages)

## 🎯 Usage

1. **Open the app** in your browser at your GitHub Pages URL
2. **Configure parameters** in the left sidebar:
   - Number of bits to transmit (50-500)
   - QBER threshold (0.05-0.20)
   - Random seed for reproducibility
   - Maximum display bits for visualization
3. **Select scenario**:
   - **No Eavesdropper**: Secure transmission (QBER ≈ 0%)
   - **With Eavesdropper**: Eve intercepts with configurable probability
   - **Compare Both**: Side-by-side comparison of both scenarios
4. **Click "Run Simulation"** to execute
5. **Explore results**:
   - View metrics (transmitted bits, sifted bits, QBER, final key length)
   - Analyze interactive timeline visualizations
   - Examine detailed data tables
   - Compare security with/without eavesdropper

## 📊 Understanding the Visualizations

### Alice's Transmitted Bits
- **Cyan bars** (height 0.2): Represents 0-bits
- **Navy bars** (height 1.0): Represents 1-bits
- Shows the quantum states Alice prepares

### Base Matching
- **Lime green**: Matching bases (bits kept after sifting)
- **Crimson**: Mismatched bases (bits discarded)
- Approximately 50% match rate due to random basis choices

### Transmission Results
- **Forest green**: Correct transmission (no error)
- **Red**: Transmission error detected
- **Light gray**: Bit not used (basis mismatch)

## 🔐 About BB84 Protocol

The BB84 protocol, invented by Charles Bennett and Gilles Brassard in 1984, is the first quantum cryptography protocol. It uses quantum mechanics principles to:

- Enable secure key distribution between two parties (Alice and Bob)
- Detect eavesdropping through quantum measurement disturbance
- Guarantee information-theoretic security

### Key Concepts

1. **Quantum States**: Alice encodes bits in quantum states using two bases
2. **Basis Sifting**: Only bits measured with matching bases are kept
3. **Error Detection**: QBER reveals eavesdropping attempts
4. **Privacy Amplification**: Compresses key to remove potential Eve's information

### Security Metrics

- **QBER (Quantum Bit Error Rate)**: Percentage of errors in sifted bits
- **Threshold**: Typically ~11% (higher indicates eavesdropping)
- **Without Eve**: QBER ≈ 0% (natural errors only)
- **With Eve (50% intercept)**: QBER ≈ 25% (detectable!)

## 🔧 Local Development (Optional)

If you want to run locally with Streamlit:

1. Install dependencies:
   ```bash
   pip install streamlit numpy pandas matplotlib
   ```

2. Run the app:
   ```bash
   streamlit run streamlit_app.py
   ```

3. Open browser at `http://localhost:8501`

**Note**: No Qiskit required! The pure Python implementation works locally and on the web.

## 📝 Files Included

- **`index.html`**: Main file for GitHub Pages deployment with stlite (required)
- **`streamlit_app.py`**: Standalone Streamlit app for local development (optional)
- **`README.md`**: This documentation

## ⚠️ Important Notes

1. **First Load**: The app takes 5-15 seconds to load initially as it downloads numpy, pandas, and matplotlib
2. **Browser Compatibility**: Works best in Chrome, Firefox, Safari, and Edge (latest versions)
3. **Performance**: Handles 500+ bits smoothly in the browser
4. **Offline Capability**: After first load, the app can work offline (packages are cached)
5. **No Qiskit**: This pure Python version is faster and more compatible than Qiskit-based versions

## 🐛 Troubleshooting

### App doesn't load
- Wait 15-20 seconds for initial package download
- Check browser console for errors (press F12)
- Try a different modern browser
- Clear browser cache (Ctrl+Shift+Delete) and reload
- Try incognito/private browsing mode

### GitHub Pages not working
- Ensure repository is **public** (required for free Pages)
- Verify `index.html` is in the **root directory** (not in a subfolder)
- Check that GitHub Pages is enabled in **Settings → Pages**
- Wait 5-10 minutes after enabling Pages
- Check the **Actions** tab for deployment status

### Simulation shows unexpected results
- **QBER = 0 without Eve**: Expected! Perfect transmission.
- **QBER > 0 with Eve**: Expected! Eavesdropping causes errors.
- If QBER = 0 with Eve, it's just random chance (try different seed)

### "Package not found" error
- Make sure you're using the latest `index.html` 
- Old versions may reference Qiskit (not compatible)
- The correct requirements are: `["numpy", "pandas", "matplotlib"]`

## 💡 Expected Behavior

| Scenario | QBER | Status | Explanation |
|----------|------|--------|-------------|
| No Eve | ~0% | SECURE | Perfect transmission, no interference |
| Eve 50% intercept | ~25% | INSECURE | Eve's measurement disturbs ~50% of intercepted bits |
| Eve 100% intercept | ~50% | INSECURE | Maximum disturbance from full interception |

## 📚 Learn More

- [BB84 Protocol (Wikipedia)](https://en.wikipedia.org/wiki/BB84)
- [Quantum Cryptography Basics](https://en.wikipedia.org/wiki/Quantum_cryptography)
- [Streamlit Documentation](https://docs.streamlit.io/)
- [stlite Repository](https://github.com/whitphx/stlite)
- [Pyodide - Python in WebAssembly](https://pyodide.org/)

## 🎓 Educational Value

This simulator is perfect for:
- **Students** learning quantum cryptography concepts
- **Educators** demonstrating BB84 protocol in lectures
- **Researchers** quickly testing BB84 scenarios
- **Enthusiasts** exploring quantum information theory

The pure Python implementation makes it accessible while remaining scientifically accurate.

## 📄 License

This project is open source and available for educational purposes.

## 🤝 Contributing

Feel free to fork, modify, and enhance this simulator! Ideas for contributions:
- Add more quantum protocols (E91, B92)
- Implement additional visualizations
- Add noise and loss models
- Create educational tutorials

If you find bugs or have suggestions, please open an issue on GitHub.

## 👏 Acknowledgments

- **Charles Bennett & Gilles Brassard** for inventing the BB84 protocol (1984)
- **Streamlit team** for the amazing web framework
- **stlite developers** for making Streamlit serverless
- **Pyodide project** for Python in WebAssembly
- **Quantum cryptography community** for educational resources

---

**Made with ❤️ for quantum cryptography education**

*Note: This simulator is for educational purposes. Real quantum key distribution systems use actual photons and quantum hardware.*
