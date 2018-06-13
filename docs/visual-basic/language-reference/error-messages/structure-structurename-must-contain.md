---
title: Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený &#39;vlastní&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594495"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Struktura &#39; &lt;%{structurename/&gt; &#39; musí obsahovat alespoň jednu instanci členské proměnné nebo deklaraci události alespoň jedna instance nesmí být označený &#39;vlastní&#39;
Definice struktury nezahrnuje všechny sdíleném proměnné nebo sdíleném nevlastní události.  
  
 Proměnné nebo událost, která platí pro každou konkrétní instanci místo (sdíleném) na všechny instance souhrnně musí mít každý struktura ([sdílené](../../../visual-basic/language-reference/modifiers/shared.md)). Sdíleném konstanty, vlastnosti a postupů nevyhovují tento požadavek. Kromě toho, pokud nejsou žádné sdíleném proměnné a jenom jedna sdíleném událost, že událost nemůže být `Custom` událostí.  
  
 **ID chyby:** BC30941  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte alespoň jednu proměnnou nebo událost, která není `Shared`. Pokud definujete jen jednu událost, musí být nevlastní, jakož i sdíleném.  
  
## <a name="see-also"></a>Viz také  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Postupy: Definice struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
