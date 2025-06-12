# VCF to 23andMe Converter

A simple Python script to convert VCF (Variant Call Format) genetic data files to 23andMe raw data format (v3 or v5).

## 🧬 About

Many genetic analysis services like Promethease, GEDmatch, and MyHeritage accept 23andMe raw data format but may have issues with VCF files. This converter helps bridge that gap by transforming your VCF genetic data into a compatible 23andMe format.

## 🚀 Features

- Converts VCF v4.x files to 23andMe format
- Supports both 23andMe v3 and v5 output formats
- Simple command-line interface
- Preserves rsID, chromosome, position, and genotype information
- Handles common genotype formats (0/0, 0/1, 1/0, 1/1)

## 📋 Requirements

- Python 3.x
- No external dependencies required

## 💻 Installation

```bash
git clone https://github.com/yourusername/vcf-to-23andme.git
cd vcf-to-23andme
```

## 🔧 Usage

### Basic usage (outputs v5 format by default):
```bash
python vcf_to_23andme.py input.vcf output.txt
```

### Specify output format:
```bash
# For 23andMe v5 format (recommended)
python vcf_to_23andme.py input.vcf output_v5.txt v5

# For 23andMe v3 format
python vcf_to_23andme.py input.vcf output_v3.txt v3
```

## 📝 Input/Output Examples

### Input VCF format:
```
##fileformat=VCFv4.2
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO	FORMAT	sample
chr1	752721	rs3131972	A	G	.	.	.	GT	1/1
chr1	759036	rs114525117	G	A	.	.	.	GT	0/0
```

### Output 23andMe format:
```
# rsid	chromosome	position	genotype
rs3131972	1	752721	GG
rs114525117	1	759036	GG
```

## 🔍 Genotype Conversion

| VCF Genotype | Meaning | 23andMe Format |
|--------------|---------|----------------|
| 0/0 | Homozygous reference | REF + REF |
| 0/1 or 1/0 | Heterozygous | REF + ALT |
| 1/1 | Homozygous alternate | ALT + ALT |
| ./. | No call | -- |

## 🌐 Compatible Services

The converted files should work with:
- [Promethease](https://promethease.com) - Personal DNA analysis
- [GEDmatch](https://www.gedmatch.com) - Genetic genealogy
- [MyHeritage DNA](https://www.myheritage.com/dna) - Family tree building
- [Genetic Genie](https://geneticgenie.org) - Methylation and detox analysis
- [Codegen.eu](https://codegen.eu) - Free genetic reports

## ⚠️ Limitations

- Only processes simple VCF files with GT (genotype) information
- Does not handle multi-allelic variants
- Assumes human genome build GRCh37/hg19
- Quality scores and filters from VCF are not preserved

## 🤝 Contributing

Feel free to open issues or submit pull requests if you find bugs or have suggestions for improvements.

## 📄 License

This project is released into the public domain. Feel free to use it however you like.

## ❓ Troubleshooting

### Common Issues:

**"File format not recognized"**
- Make sure your output file has a `.txt` extension
- Some services may require specific file encoding (UTF-8)

**"Missing genetic data"**
- Check that your VCF file contains genotype (GT) information
- Ensure the VCF follows standard format specifications

**"Service still rejecting the file"**
- Try using v3 format instead of v5 (some older services prefer v3)
- Check if the service has file size limitations

## 🙏 Acknowledgments

Created to help people analyze their genetic data across different platforms. Special thanks to the bioinformatics community for maintaining open standards.

---

**Disclaimer**: This tool is for educational and research purposes only. Always consult healthcare professionals for medical advice regarding genetic information.
