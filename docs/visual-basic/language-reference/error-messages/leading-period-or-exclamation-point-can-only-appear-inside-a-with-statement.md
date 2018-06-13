---
title: Úvodní &#39;. &#39; nebo &#39;! &#39; může vyskytovat pouze uvnitř &#39;s&#39; – příkaz
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 7802b8e0aaf3dff83d5bfbe11f0b8bb1b5bb46cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589444"
---
# <a name="leading-3939-or-3939-can-only-appear-inside-a-39with39-statement"></a>Úvodní &#39;. &#39; nebo &#39;! &#39; může vyskytovat pouze uvnitř &#39;s&#39; – příkaz
Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně. Přístup ke členu (`.`) a přístup ke členu slovníku (`!`) vyžadují zadání elementu, který obsahuje člen výrazu. Ta musí okamžitě zobrazí nalevo přistupujícího objektu nebo jako cíl `With` bloku obsahující přístup ke členu.  
  
 **ID chyby:** BC30157  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že `With` bloku je správně naformátován.  
  
2.  Pokud není žádná `With` blokovat, přidejte výraz nalevo od přistupujícího objektu, která vyhodnotí definovaný element obsahující člena.  
  
## <a name="see-also"></a>Viz také  
 [Speciální znaky v kódu](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
