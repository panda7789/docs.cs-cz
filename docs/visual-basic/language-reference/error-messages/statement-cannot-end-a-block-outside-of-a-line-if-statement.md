---
title: Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0cee52f0ca00395d93c469aae6498fd3793f1085
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266309"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Příkaz nemůže ukončit blok mimo řádek s příkazem 'If'.
Jeden řádek `If` příkaz obsahuje několik příkazy oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jedním řádkem `If`. Jednořádkový `If` příkazy nepoužívejte `End If` příkazu.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout jedním řádkem `If` příkazu mimo blok ovládací prvek, který obsahuje `End If` příkazu.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
