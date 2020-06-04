---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 11e866d9a8da7ad1ecc5f788fc31f6ac96d32f2c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409826"
---
# <a name="bad-file-name-or-number"></a>Chybný název souboru nebo číslo
Při pokusu o přístup k zadanému souboru došlo k chybě. Mezi možné příčiny této chyby patří:  
  
- Příkaz odkazuje na soubor s názvem nebo číslem souboru, který nebyl zadán v `FileOpen` příkazu nebo který byl zadán v `FileOpen` příkazu, ale byl následně uzavřen.  
  
- Příkaz odkazuje na soubor s číslem, který se nachází mimo rozsah čísel souborů.  
  
- Příkaz odkazuje na název souboru nebo číslo, které není platné.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Přesvědčte se, zda je název souboru zadán v `FileOpen` příkazu. Všimněte si, že pokud jste příkaz vyvolali `FileClose` bez argumentů, možná jste omylem zavřeli všechny otevřené soubory.  
  
2. Pokud kód generuje čísla souborů algorithmically, ujistěte se, že jsou čísla platná.  
  
3. Zkontrolujte názvy souborů a ujistěte se, že odpovídají konvencím operačního systému.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Zásady vytváření názvů jazyka Visual Basic](../../programming-guide/program-structure/naming-conventions.md)
