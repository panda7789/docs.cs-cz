---
title: Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Příkaz nemůže ukončit blok mimo řádek s &#39;Pokud&#39; – příkaz
Jeden řádek `If` příkaz obsahuje několik příkazů oddělené dvojtečkou (:), z nichž jeden je `End` příkaz pro řídicí blok mimo jeden řádek `If`. Jeden řádek `If` příkazy se nedoporučuje používat `End If` příkaz.  
  
 **ID chyby:** BC32005  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přesunout jednom řádku `If` příkaz mimo řídicí blok, který obsahuje `End If` příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
