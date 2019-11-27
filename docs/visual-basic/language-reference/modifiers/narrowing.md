---
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351479"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některé z možných hodnot původní třídy nebo struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Převod s klíčovým slovem zúžení  
 Postup převodu musí kromě `Narrowing`zadat `Public Shared`.  
  
 Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat. Příklady jsou `Long` pro `Integer`, `String` na `Date`a základní typ pro odvozený typ. Tento poslední převod je zúžený, protože základní typ nemusí obsahovat všechny členy odvozeného typu, a proto není instancí odvozeného typu.  
  
 Pokud je `Option Strict` `On`, musí používat kód `CType` pro všechny zužující převody.  
  
 Klíčové slovo `Narrowing` lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
