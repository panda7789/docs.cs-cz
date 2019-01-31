---
title: Struktura '<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a8a85f4f089de9be6f2ecadac05256b30d3014b0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267453"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Struktura '\<%{structurename/ >' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako 'Custom'
Definice struktury neobsahuje žádné nesdílených proměnných nebo nesdílené nevlastních událostí.  
  
 Každý struktura musí mít proměnná nebo událost, která se vztahuje na každý konkrétní instanci místo (nesdílené) do všech instancí souhrnně ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Tento požadavek nesplňují nesdílené konstanty, vlastnosti a postupy. Kromě toho, pokud neexistují žádné nesdílených proměnných a jenom jedna událost nesdílené, tuto událost nemůže být `Custom` událostí.  
  
 **ID chyby:** BC30941  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Definujte alespoň jednu proměnnou nebo událostí, které nejsou `Shared`. Pokud definujete jen jednu událost, musí být nevlastní, jakož i nesdílené.  
  
## <a name="see-also"></a>Viz také:
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Postupy: Deklarace struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
