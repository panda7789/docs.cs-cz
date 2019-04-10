---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 2e5d4a3ddd66df85dc4758e22b36ac1ed495659a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322157"
---
# <a name="bad-file-name-or-number"></a>Chybný název souboru nebo číslo
Při pokusu o přístup k zadanému souboru došlo k chybě. Mezi možné příčiny této chyby patří:  
  
-   Příkaz odkazuje na soubor s názvem souboru nebo číslo, který nebyl zadán v `FileOpen` příkazu nebo, který byl zadán v `FileOpen` prohlášení, avšak byla následně uzavřen.  
  
-   Příkaz odkazuje na soubor s číslo, které je mimo rozsah čísel souborů.  
  
-   Příkaz odkazuje na název souboru nebo číslo, které není platný.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že byl zadán název souboru `FileOpen` příkazu. Poznámka: Pokud jste vyvolali `FileClose` příkaz bez argumentů, mohou neúmyslně neukončíte všechny otevřené soubory.  
  
2. Pokud váš kód algorithmically generuje soubor čísla, zkontrolujte, zda že jsou čísla platné.  
  
3. Zkontrolujte názvy souborů, abyste měli jistotu, že jsou v souladu s konvencí operačního systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
