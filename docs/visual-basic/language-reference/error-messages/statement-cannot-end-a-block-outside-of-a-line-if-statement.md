---
title: Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400315"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
Jednořádkový `If` příkaz obsahuje několik příkazů, které jsou odděleny dvojtečkami (:), jeden z nich je `End` příkaz pro řídicí blok mimo jeden řádek `If` . Jednořádkové `If` příkazy nepoužívají `End If` příkaz.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesune příkaz na jeden řádek `If` mimo řídicí blok, který obsahuje `End If` příkaz.  
  
## <a name="see-also"></a>Viz také

- [If...Then...Else – příkaz](../statements/if-then-else-statement.md)
