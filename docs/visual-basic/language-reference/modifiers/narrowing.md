---
title: Narrowing (Visual Basic)
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
ms.openlocfilehash: 54a18d0cc10e42829b48b0ef75bb77ab0d47b45f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí obsahovat některé možné hodnoty z původní třídu nebo strukturu.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Převádění s Narrowing – klíčové slovo  
 Musíte zadat procesu převodu `Public Shared` kromě `Narrowing`.  
  
 Zužující převody není vždy úspěch v době běhu a může selhat nebo dojít ke ztrátě dat. Příklady `Long` k `Integer`, `String` k `Date`a základní typ pro odvozený typ. Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozený typ a proto není instance odvozeného typu.  
  
 Pokud `Option Strict` je `On`, využívání kód musíte použít `CType` pro všechny zužující převody.  
  
 `Narrowing` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
