---
title: Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 85573099ec0a3f8a23c17bdf384c4c105f9157df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825791"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
Jeden řádek `If` příkaz obsahuje několik příkazy oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jedním řádkem `If`. Jednořádkový `If` příkazy nepoužívejte `End If` příkazu.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout jedním řádkem `If` příkazu mimo blok ovládací prvek, který obsahuje `End If` příkazu.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
