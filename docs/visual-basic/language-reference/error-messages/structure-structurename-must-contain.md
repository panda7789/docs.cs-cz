---
title: Struktura '<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 7b5bda7b1a2ae37eb509c736deae1652dc5e6ab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374015"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Struktura '\<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
Definice struktury neobsahuje žádné nesdílené proměnné ani nesdílené nesdílené události.  
  
 Každá struktura musí mít buď proměnnou, nebo událost, která se vztahuje na jednotlivé konkrétní instance (nesdílené) místo na všechny instance souhrnně ([sdílené](../modifiers/shared.md)). Nesdílené konstanty, vlastnosti a procedury nesplňují tento požadavek. Kromě toho, pokud nejsou žádné nesdílené proměnné a jenom jedna nesdílená událost, tato událost nemůže být `Custom` událost.  
  
 **ID chyby:** BC30941  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Definujte alespoň jednu proměnnou nebo událost, která není `Shared` . Pokud definujete jenom jednu událost, musí být nevlastní i nesdílená.  
  
## <a name="see-also"></a>Viz také

- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Postupy: Deklarace struktury](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure – příkaz](../statements/structure-statement.md)
