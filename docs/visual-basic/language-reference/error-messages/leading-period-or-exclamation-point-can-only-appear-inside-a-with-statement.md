---
title: Úvodní &#39;. &#39; nebo &#39;! &#39; může být použito pouze uvnitř &#39;s&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: e64318d4ececbd887f55a1a202cc2d58c90c8fc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625949"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Úvodní &#39;. &#39; nebo &#39;! &#39; může být použito pouze uvnitř &#39;s&#39; – příkaz
Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně. Přístup ke členu (`.`) a přístup ke členu slovník (`!`) vyžadují výraz určující prvek, který obsahuje člena. Toto musí být uvedena ihned na levé straně přístupového objektu nebo jako cíl `With` bloku, který obsahuje přístup ke členu.  
  
 **ID chyby:** BC30157  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, `With` blok je správně formátovaný.  
  
2.  Pokud není žádný `With` blokovat, zadejte nějaký výraz nalevo od přístupový objekt, který se vyhodnotí na definovaný element obsahující tento člen.  
  
## <a name="see-also"></a>Viz také:
- [Speciální znaky v kódu](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
