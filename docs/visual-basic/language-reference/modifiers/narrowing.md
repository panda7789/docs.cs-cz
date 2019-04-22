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
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838843"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některou z možných hodnot původní třídy nebo struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Pomocí klíčového slova zužující převod  
 Proces převodu musíte zadat `Public Shared` kromě `Narrowing`.  
  
 Zužující převody nejsou vždy v době spuštění úspěšné a může selhat nebo ztrátě dat se vám účtovat. Mezi příklady patří `Long` k `Integer`, `String` k `Date`a základního typu odvozeného typu. Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozeného typu a proto není instance odvozeného typu.  
  
 Pokud `Option Strict` je `On`, využívání kódu musí používat `CType` pro všechny zužujících převodů.  
  
 `Narrowing` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
