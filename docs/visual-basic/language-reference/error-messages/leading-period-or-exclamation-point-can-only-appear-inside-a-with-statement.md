---
title: Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 15390fb506fe9bca10f6917f5b26451a5569bece
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322846"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.
Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku probíhá, aniž by výraz na levé straně. Přístup ke členu (`.`) a přístup ke členu slovník (`!`) vyžadují výraz určující prvek, který obsahuje člena. Toto musí být uvedena ihned na levé straně přístupového objektu nebo jako cíl `With` bloku, který obsahuje přístup ke členu.  
  
 **ID chyby:** BC30157  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, `With` blok je správně formátovaný.  
  
2. Pokud není žádný `With` blokovat, zadejte nějaký výraz nalevo od přístupový objekt, který se vyhodnotí na definovaný element obsahující tento člen.  
  
## <a name="see-also"></a>Viz také:

- [Speciální znaky v kódu](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [Příkaz With...End With](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
