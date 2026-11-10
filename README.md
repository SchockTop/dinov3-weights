# DINOv3 weights

Unmodified copies of Meta's model weights, stored directly in this git repository. Upstream: https://github.com/facebookresearch/dinov3

**License:** these files are distributed under Meta's DINOv3 License, see [LICENSE](LICENSE).
By downloading or using them you agree to those terms. This mirror does not relicense anything.

## Get the weights

Everything is in the repo itself (no releases, no Git LFS). GitHub allows at most 100 MB per file,
so each large file is stored as `<name>.part000`, `<name>.part001`, ... next to its config files.

```
git clone --depth 1 https://github.com/SchockTop/dinov3-weights.git
cd dinov3-weights
python join.py
```

`join.py` works offline (standard library only): it joins the parts into the model files below and checks
the SHA256. `python join.py --only <folder>` joins one variant, `--delete-parts` frees the space afterwards.

Without Python, join by hand and compare the SHA256 with the table:

```
:: Windows (cmd)
copy /b "dinov3-vitl16-pretrain-lvd1689m\model.safetensors.part*" "dinov3-vitl16-pretrain-lvd1689m\model.safetensors"
certutil -hashfile "dinov3-vitl16-pretrain-lvd1689m\model.safetensors" SHA256

# Linux / macOS
cat dinov3-vitl16-pretrain-lvd1689m/model.safetensors.part* > dinov3-vitl16-pretrain-lvd1689m/model.safetensors && sha256sum dinov3-vitl16-pretrain-lvd1689m/model.safetensors
```

## Contents

- `dinov3-vitl16-pretrain-lvd1689m/`: ViT-L/16 (LVD-1689M), Hugging Face `transformers` format
- `dinov3-vith16plus-pretrain-lvd1689m/`: ViT-H+/16 (LVD-1689M), original `.pth` for the Meta repo / torch.hub

| File | Size | Parts | SHA256 |
|---|---|---|---|
| `dinov3-vitl16-pretrain-lvd1689m/model.safetensors` | 1.21 GB | 13 | `dcb2e45127cccbf1601e5f42fef165eea275c8e5213197e8dcf3f48822718179` |
| `dinov3-vith16plus-pretrain-lvd1689m/dinov3_vith16plus_pretrain_lvd1689m-7c1da9a5.pth` | 3.36 GB | 34 | `7c1da9a54b3bdb333f5ebc42e404b7f19b1b5bed504877623c9dc87397f41488` |

`.pt` / `.pth` files are pickle based: load them with `torch.load(..., weights_only=True)`.
