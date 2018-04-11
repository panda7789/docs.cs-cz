---
title: Chybný název souboru nebo číslo
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
