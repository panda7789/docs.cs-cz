---
title: Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574713"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz
Jeden řádek `If` příkaz obsahuje několik příkazy oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jedním řádkem `If`. Jednořádkový `If` příkazy nepoužívejte `End If` příkazu.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout jedním řádkem `If` příkazu mimo blok ovládací prvek, který obsahuje `End If` příkazu.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
