---
title: Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397321"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a>Úvodní operátor '.' nebo '!' může být použit pouze uvnitř příkazu 'With'.
Tečka (.) nebo vykřičník (!), který není uvnitř `With` bloku, nastávají bez výrazu na levé straně. Přístup ke členu ( `.` ) a přístup ke členu slovníku ( `!` ) vyžadují výraz určující prvek, který obsahuje člena. Ta se musí objevit hned nalevo od přístupového objektu nebo jako cíl `With` bloku obsahujícího přístup ke členu.  
  
 **ID chyby:** BC30157  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby byl `With` blok správně naformátován.  
  
2. Pokud není žádný `With` blok, přidejte výraz nalevo od přístupového objektu, který se vyhodnotí na definovaný element obsahující člena.  
  
## <a name="see-also"></a>Viz také

- [Speciální znaky v kódu](../../programming-guide/program-structure/special-characters-in-code.md)
- [With...End With – příkaz](../statements/with-end-with-statement.md)
