---
title: Rna Transcription
date: 2025-08-19T17:49:18+05:30
---

``` python
"""
Determine the RNA complement of a given DNA sequence.
"""

def to_rna(dna_strand: str) -> str:
    result = []
    for strand in dna_strand:
        match strand:
            case "G":
                result.append("C")
            case "C":
                result.append("G")
            case "T":
                result.append("A")
            case "A":
                result.append("U")
    return "".join(result)
```