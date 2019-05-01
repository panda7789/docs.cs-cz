---
title: Struktura '<structurename>' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance, která není označena jako 'Custom'.
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055105"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Struktura '\<%{structurename/ >' musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako 'Custom'
Definice struktury neobsahuje žádné nesdílených proměnných nebo nesdílené nevlastních událostí.  
  
 Každý struktura musí mít proměnná nebo událost, která se vztahuje na každý konkrétní instanci místo (nesdílené) do všech instancí souhrnně ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Tento požadavek nesplňují nesdílené konstanty, vlastnosti a postupy. Kromě toho, pokud neexistují žádné nesdílených proměnných a jenom jedna událost nesdílené, tuto událost nemůže být `Custom` událostí.  
  
 **ID chyby:** BC30941  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Definujte alespoň jednu proměnnou nebo událostí, které nejsou `Shared`. Pokud definujete jen jednu událost, musí být nevlastní, jakož i nesdílené.  
  
## <a name="see-also"></a>Viz také:

- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Postupy: Deklarace struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
