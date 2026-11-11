# Steganography Detection and Extraction in Forensic Evidence

A digital forensics lab completed for IST 476 (Applied Information Security) at Syracuse University. The goal was to determine whether steganography was used to hide data on a training evidence drive image, and if so, to find and recover it.

## Summary

Hash matching in Paraben's E3 uncovered a disguised copy of the steganography tool OpenPuff, renamed `temp17.exe.exe`. StegExpose LSB steganalysis then flagged `lakeview.bmp` as a carrier image holding an estimated 31 KB of hidden data, even though the image looked completely normal. Using a passphrase found in a Readme file in the same folder, OpenPuff recovered a concealed file listing Chicago addresses with GPS coordinates. All extraction was done on exported copies to preserve the original evidence.

## Tools

| Tool | Purpose |
| --- | --- |
| Paraben's E3 | Hash-based search of the evidence image and file export |
| StegExpose | Statistical (LSB) steganalysis of exported images |
| Microsoft Paint | Visual inspection of the flagged image |
| OpenPuff | Extraction of the hidden file with the recovered passphrase |

## Key Takeaways

- **File names prove nothing.** The renamed tool was still caught because its MD5 hash matched a known steganography tool.
- **Hidden data can be invisible.** LSB embedding left no visual trace, but it shifted the image's statistics enough for StegExpose to detect it.
- **Detection isn't extraction.** Recovering the data required both the right tool and the passphrase.

## MITRE ATT&CK Mapping

| Technique | Name |
| --- | --- |
| T1027.003 | Obfuscated Files or Information: Steganography |
| T1001.002 | Data Obfuscation: Steganography |
| T1036 | Masquerading |

## Repository Contents

- `IST476_SteganographyBonusLab_JamesOLeary.pdf` - full lab report with procedure, screenshots, analysis, and references

## References

- Boehm, B. (2014). *StegExpose: A tool for detecting LSB steganography.* arXiv:1410.6656
- Fridrich, J. (2009). *Steganography in Digital Media.* Cambridge University Press
- Kent, K., et al. (2006). *Guide to Integrating Forensic Techniques into Incident Response* (NIST SP 800-86)
- MITRE ATT&CK. [T1027.003: Steganography](https://attack.mitre.org/techniques/T1027/003/)
