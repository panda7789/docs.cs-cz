---
title: Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako &#39;vlastní&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: d8c654c212a459d40c6cf20cd62c3e0fcda8511b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603778"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu členskou proměnnou instance nebo alespoň jednu deklaraci události instance není označena jako &#39;vlastní&#39;
Definice struktury neobsahuje žádné nesdílených proměnných nebo nesdílené nevlastních událostí.  
  
 Každý struktura musí mít proměnná nebo událost, která se vztahuje na každý konkrétní instanci místo (nesdílené) do všech instancí souhrnně ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Tento požadavek nesplňují nesdílené konstanty, vlastnosti a postupy. Kromě toho, pokud neexistují žádné nesdílených proměnných a jenom jedna událost nesdílené, tuto událost nemůže být `Custom` událostí.  
  
 **ID chyby:** BC30941  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Definujte alespoň jednu proměnnou nebo událostí, které nejsou `Shared`. Pokud definujete jen jednu událost, musí být nevlastní, jakož i nesdílené.  
  
## <a name="see-also"></a>Viz také:
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Postupy: Deklarace struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
