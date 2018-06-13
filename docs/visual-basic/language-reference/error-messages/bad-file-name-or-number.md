---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 903be68e71ad590b4b669545afd077175534ef4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585564"
---
# <a name="bad-file-name-or-number"></a>Chybný název souboru nebo číslo
Došlo k chybě při pokusu o přístup k zadanému souboru. Mezi možné příčiny této chyby patří:  
  
-   Příkaz odkazuje na soubor s názvem souboru nebo číslo, který nebyl specifikován v `FileOpen` v byl zadán příkaz nebo který `FileOpen` příkaz ale byl následně uzavřen.  
  
-   Příkaz odkazuje na soubor s číslo, které je mimo rozsah čísel souboru.  
  
-   Příkaz odkazuje na název souboru nebo číslo, který není platný.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že v je zadán název souboru `FileOpen` příkaz. Všimněte si, že pokud je volána `FileClose` příkaz bez argumentů, může nechtěně ukončení všech otevřených souborů.  
  
2.  Pokud váš kód je algorithmically generování čísel soubor, zkontrolujte, zda že jsou čísla platné.  
  
3.  Zkontrolujte názvy souborů a ujistěte se, že jsou v souladu s konvence operačního systému.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
