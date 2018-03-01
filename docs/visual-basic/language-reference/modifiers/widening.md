---
title: "Rozšíření (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a>Rozšíření (Visual Basic)
Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu typ, který může obsahovat všechny možné hodnoty z původní třídu nebo strukturu.  
  
## <a name="converting-with-the-widening-keyword"></a>Převádění s rozšiřující – klíčové slovo  
 Musíte zadat procesu převodu `Public Shared` kromě `Widening`.  
  
 Rozšiřující převody proběhnout úspěšně v době běhu a nikdy dojít ke ztrátě dat. Příklady `Single` k `Double`, `Char` k `String`a k jeho základní typ odvozený typ. Tento poslední převod je rozšíření, protože obsahuje všechny členy základní typ odvozený typ a proto je instance základního typu.  
  
 Není nutné používat kód náročné `CType` pro rozšiřující převody, i když `Option Strict` je `On`.  
  
 `Widening` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Například zobrazit definice rozšíření a zúžení operátory převodu [postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Viz také  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Zužující](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Postupy: definice operátora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Postupy: definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
