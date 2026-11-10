# DINOv3 weights

Unmodified copies of Meta's model weights, mirrored for easy download. Upstream: https://github.com/facebookresearch/dinov3

**License:** these files are distributed under Meta's DINOv3 License, see [LICENSE](LICENSE).
By downloading or using them you agree to those terms. This mirror does not relicense anything.

## Get the weights

The large files are GitHub release assets (split into parts below 2 GB); small config files are in the repo.

```
git clone https://github.com/SchockTop/dinov3-weights.git
cd dinov3-weights
python download.py
```

`download.py` (standard library only) fetches the parts, joins them into the folders below and checks the SHA256.
Use `python download.py --only <folder>` for a single variant.

## Contents

- `dinov3-vitl16-pretrain-lvd1689m/`: ViT-L/16 (LVD-1689M), Hugging Face `transformers` format
- `dinov3-vith16plus-pretrain-lvd1689m/`: ViT-H+/16 (LVD-1689M), original `.pth` for the Meta repo / torch.hub

| File | Size | SHA256 |
|---|---|---|
| `dinov3-vitl16-pretrain-lvd1689m/model.safetensors` | 1.21 GB | `dcb2e45127cccbf1601e5f42fef165eea275c8e5213197e8dcf3f48822718179` |
| `dinov3-vith16plus-pretrain-lvd1689m/dinov3_vith16plus_pretrain_lvd1689m-7c1da9a5.pth` | 3.36 GB | `7c1da9a54b3bdb333f5ebc42e404b7f19b1b5bed504877623c9dc87397f41488` |

`.pt` / `.pth` files are pickle based: load them with `torch.load(..., weights_only=True)`.
