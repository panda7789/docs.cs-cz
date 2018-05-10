---
title: Rozšíření (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="widening-visual-basic"></a>Rozšíření (Visual Basic)
Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu typ, který může obsahovat všechny možné hodnoty z původní třídu nebo strukturu.  
  
## <a name="converting-with-the-widening-keyword"></a>Převádění s rozšiřující – klíčové slovo  
 Musíte zadat procesu převodu `Public Shared` kromě `Widening`.  
  
 Rozšiřující převody proběhnout úspěšně v době běhu a nikdy dojít ke ztrátě dat. Příklady `Single` k `Double`, `Char` k `String`a k jeho základní typ odvozený typ. Tento poslední převod je rozšíření, protože obsahuje všechny členy základní typ odvozený typ a proto je instance základního typu.  
  
 Není nutné používat kód náročné `CType` pro rozšiřující převody, i když `Option Strict` je `On`.  
  
 `Widening` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Například zobrazit definice rozšíření a zúžení operátory převodu [postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
