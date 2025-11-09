# Wireless PHY Toolkit

**Clean, tested implementations of wireless PHY algorithms.**

## About This Project

I'm Konstantinos Dovelos, a Senior Wireless Communications Engineer.

**Why I'm building this:**

After a decade of implementing PHY algorithms in MATLAB and guiding FPGA teams, I'm learning to write production-quality software. This repo is where I'm:

- **Re-implementing algorithms I already know** (synchronization, AGC, modulation) with proper software engineering practices
- **Building a personal library** I can reuse across projects
- **Creating a portfolio** that demonstrates both domain expertise and coding skills
- **Learning in public** - documenting my journey from wireless expert to wireless expert who codes

**Current Status:** 🏗️ **Active Development** - Starting with foundational algorithms, adding new implementations weekly.

**Who this might help:**
- Engineers learning PHY implementation (reference code with explanations)
- FPGA developers needing validated Python models before hardware implementation  
- Researchers wanting baseline implementations for benchmarking
- My future self who forgets how I implemented things

## 🎯 Project Philosophy

**"Learning in public, building for real"**

This isn't vaporware or academic exercise - every algorithm:
- Solves a problem I've actually faced in my work
- Is implemented the way I wish I had found it when I needed it
- Includes the context and references I had to hunt down myself
- Has tests covering the edge cases I've debugged on hardware

If it helps other engineers along the way, that's a bonus. If it leads to future opportunities, even better.

## 🚀 Current Algorithms

### Synchronization
- **Schmidl-Cox timing synchronization** - OFDM preamble detection with plateau removal
  - Reference: Schmidl & Cox, IEEE Trans. Comm., 1997
  - Status: ✅ Tested, documented
  - Next: Add frequency offset estimation

### Coming Soon
- AGC algorithms (log-domain, RSSI-based)
- QPSK/QAM modulation with pulse shaping
- Channel estimation (LS, MMSE, compressed sensing)
- Interference nulling and beamforming
- OFDM symbol timing and CFO correction

## 📦 Installation

```bash
git clone https://github.com/yourusername/wireless-phy-toolkit.git
cd wireless-phy-toolkit

# With Conda (recommended for scientific computing)
conda create -n wireless-phy python=3.11
conda activate wireless-phy
pip install -e .

# Or with pip + venv
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -e .
```

## 🔧 Quick Example

```python
import numpy as np
from wireless_phy.algorithms.synchronization import schmidl_cox_sync

# Simulate an OFDM signal with timing offset
signal = generate_ofdm_preamble()  # Your signal here
noisy_signal = add_awgn(signal, snr_db=10)

# Detect timing offset
offset, metric = schmidl_cox_sync(
    signal=noisy_signal,
    training_length=64,
    threshold=0.8
)

print(f"Detected timing offset: {offset} samples")
```

See `examples/` for complete demonstrations with visualization.

## 🧪 Testing & Quality

Every algorithm includes:
- ✅ Unit tests with known test vectors
- ✅ Tests with AWGN, fading, and impairments
- ✅ Type hints and mypy checking
- ✅ Comprehensive docstrings with references
- ✅ Example usage and plots

```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=wireless_phy --cov-report=html

# Type checking
mypy src/
```

## 🎓 My Background

**Current Role:** Senior Wireless Communications Engineer at Intracom Defense
- Leading PHY design for tactical radios, UAV communication systems, and covert sensing waveforms
- Algorithms: AGC, sync, BICM, MIMO, diversity schemes, interference nulling
- Coordinating SW/HW/RF teams and guiding FPGA implementation

**Previous Work:**
- Postdoc at Queen's University Belfast: Massive MIMO architectures for 6G
- PhD at Universitat Pompeu Fabra: Beamforming, hybrid MIMO, near-field focusing
- Antenna Engineer at Meta Materials: 5G mmWave coverage optimization
- RF Engineer: Built a radio telescope and detected the galactic hydrogen line (because it's cool)

**Publications:** [Google Scholar - Konstantinos Dovelos](https://scholar.google.com)

## 💡 Why I'm Building This

**Short term:** Learn modern software engineering while leveraging my domain expertise

**Medium term:** Build a portfolio that opens doors to remote opportunities and consulting

**Long term:** Explore whether this could become a validation platform or HLS code generation tool

**Right now:** Just shipping clean implementations, one algorithm at a time.

## 🤝 Contributing

This is a personal project, but contributions are welcome! If you:
- Find a bug or have a suggestion → Open an issue
- Want to add an algorithm → Let's discuss first (open an issue)
- Spot an error in implementation → Pull requests appreciated

**Code standards:**
- Write tests first (TDD)
- Type hints required
- Document with references to original papers
- Black formatting, pylint clean

## 📚 Philosophy

**"Fast, good, cheap - pick two" doesn't apply to software.**

With proper engineering:
- Code can be fast (NumPy/C++ when needed)
- Code can be good (tested, typed, documented)
- Code can be free (open source)

All it takes is time and discipline.

## 🔗 Connect With Me

- **LinkedIn:** [Konstantinos Dovelos](https://www.linkedin.com/in/kostis-dovelos-88219656/)
- **Email:** kostisdovelos@hotmail.com

**Following my journey?** Star this repo and check back weekly - I'm building and shipping consistently.

---

**Project Status:** 🏗️ Active Development (Week 1)  
**License:** MIT  
