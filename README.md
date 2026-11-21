# Copista / Copisteria — unofficial Pinokio launcher

An independent Pinokio launcher for [KobiMusic Copisteria](https://github.com/kobimusic/copisteria), the reader for Copista optical music recognition models.

## Install

1. In Pinokio choose **Download from URL** and enter **https://github.com/ChrisTorng/copista.pinokio**.
2. Select **Install**, then **Start**, and **Open Web UI**.
3. Upload a PDF or image; select PDF page range and the 28M (default) or 2M model.
4. Download resulting MusicXML, reading JSON, annotated HTML viewer and ZIP.

The app clones upstream under `app/source` and creates a Python 3.12 virtual environment under `app/.venv`. The Hugging Face 28M and 2M weights are downloaded during Install into the upstream model directory. The lightweight local upload interface is contributed by this launcher, not included in upstream. **Update** fast-forwards the upstream checkout without deleting any prior output saved in `app/runs`.

## Requirements

- Windows 11 x64 with an NVIDIA CUDA-capable GPU (including the RTX 3070 Laptop GPU), or Ubuntu 26.04 x64. CPU inference is also available.
- Pinokio AI bundle providing **uv**, Git and Python 3.12 provisioning. On Windows, the installer uses uv to select matching PyTorch and torchvision builds based on the installed GPU driver. For NVIDIA, check the Install log for `CUDA True` and your GPU name.
- **PDF input requires Poppler** (`pdftoppm` and `pdfimages` on PATH). On Windows use `winget install -e --id oschwartz10612.Poppler` in PowerShell and restart Pinokio. On Ubuntu use `sudo apt install poppler-utils`. For PNG or JPEG input, Poppler is optional.
- Serves at `http://127.0.0.1:50882` (loopback only). Port must be unused.
- 28M has better recognition quality in the upstream benchmark; 2M is lower-resource.
- This is for **standard staff notation**, not direct numbered notation (簡譜) recognition.
- If processing fails choose **View log**. CPU fallback is slower.

## Verification

- Upstream CLI arguments and model paths reviewed against Copisteria code.
- GitHub Actions checks JavaScript and Python syntax.
- Physical GPU inference on a Windows RTX 3070 Laptop GPU or Ubuntu RTX 4090 still needs a hardware test.

Upstream: https://github.com/kobimusic/copisteria
Models: https://huggingface.co/collections/kobimusic/copista-6ac3033f1a779b0c63ad41a9
