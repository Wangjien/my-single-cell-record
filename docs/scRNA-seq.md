<!--
 * @Author: wangje
 * @Date: 2025-12-13 21:56:05
-->
## 10X 分析工具CellRanger学习

## cellranger count

官方教程：https://www.10xgenomics.com/support/software/cell-ranger/latest/tutorials/cr-tutorial-ct

`cellranger count` 是 10x Genomics 官方用于**单细胞 RNA-seq（scRNA-seq）数据定量分析**的核心命令，主要功能是将单细胞测序的原始 fastq 文件与参考基因组比对，生成细胞级别的基因表达矩阵。

### cellranger count下载和安装

目前的cellranger版本已经更新到了Cell Ranger 10.0.0 (Nov 13, 2025)，如果需要下载历史版本，可以通过访问[https://www.10xgenomics.com/support/software/cell-ranger/downloads/previous-versions](https://www.10xgenomics.com/support/software/cell-ranger/downloads/previous-versions)进行下载。

```powershell
## 这里下载的时Cell Ranger 10.0.0版本
# 命令行使用curl下载
curl -o cellranger-10.0.0.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-10.0.0.tar.gz?Expires=1765682198&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA&Signature=SO3tn4o50UYUViprsueJpWGbkOLqzAUxH8X4fbKgtr4LxexzQFLWWc~Og9I3AUpOKrntOLVFd0TTfJ63X5EuM2jl5fwLvMPVDg2Mh4liM0Lp87qzhyY6TsxdJkRs3UuMlelp3rc2ZATBG9O5yfo-Urxgx-dY5jsnpldy0hKg58XGe8-r6CGmOI1CzGAF4qpiCgJOzRbONK7QHDFTYcKey6Xmh7PT~KPRip24kUcKiJyJzyfhGNdfSACJbJgA02kLEBb2EmZasQFvfRoY0NPMFlnVpFkIv7-p73JA~CiYERWT0awbwdkPn7n7eXItlVktXA3Z2QwiT~DJfsc8eKC2rA__"

# 命令行使用wget下载
wget -O cellranger-10.0.0.tar.gz "https://cf.10xgenomics.com/releases/cell-exp/cellranger-10.0.0.tar.gz?Expires=1765682198&Key-Pair-Id=APKAI7S6A5RYOXBWRPDA&Signature=SO3tn4o50UYUViprsueJpWGbkOLqzAUxH8X4fbKgtr4LxexzQFLWWc~Og9I3AUpOKrntOLVFd0TTfJ63X5EuM2jl5fwLvMPVDg2Mh4liM0Lp87qzhyY6TsxdJkRs3UuMlelp3rc2ZATBG9O5yfo-Urxgx-dY5jsnpldy0hKg58XGe8-r6CGmOI1CzGAF4qpiCgJOzRbONK7QHDFTYcKey6Xmh7PT~KPRip24kUcKiJyJzyfhGNdfSACJbJgA02kLEBb2EmZasQFvfRoY0NPMFlnVpFkIv7-p73JA~CiYERWT0awbwdkPn7n7eXItlVktXA3Z2QwiT~DJfsc8eKC2rA__"

# 下载完成后安装cellranger
tar -xzf cellranger-10.0.0.tar.gz

```
### cellranger count使用的参考文件下载
目前cellranger count使用的参数文件也做了更新，目前的版本为:2024-A，历史版本为：2020-A（[https://www.10xgenomics.com/support/software/cell-ranger/latest/release-notes/cr-reference-release-notes#2020-a](https://www.10xgenomics.com/support/software/cell-ranger/latest/release-notes/cr-reference-release-notes#2020-a)）。
  
  * Human reference (GRCh38) - 2024-A
  ```Powershell
  # wget 下载
  wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCh38-2024-A.tar.gz"
  
  # curl 下载
  curl -O "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCh38-2024-A.tar.gz"
 ```
* Mouse reference (GRCm39) - 2024-A
```Powershell
# wget下载
wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCm39-2024-A.tar.gz"

# curl 下载
curl -O "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-GRCm39-2024-A.tar.gz"
```
* Rat reference (mRatBN7.2) - 2024-A
```Powershell
# wget下载
wget "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-mRatBN7-2-2024-A.tar.gz"

# curl下载
curl -O "https://cf.10xgenomics.com/supp/cell-exp/refdata-gex-mRatBN7-2-2024-A.tar.gz"
```
