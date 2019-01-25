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
ms.openlocfilehash: 3b9d1ec15c6c2000fb0842abe25848f853cdf986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703705"
---
# <a name="widening-visual-basic"></a>Rozšíření (Visual Basic)
Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který může uchovat všechny možné hodnoty původní třídy nebo struktury.  
  
## <a name="converting-with-the-widening-keyword"></a>Převod pomocí rozšiřující – klíčové slovo  
 Proces převodu musíte zadat `Public Shared` kromě `Widening`.  
  
 Rozšiřující převody proběhnout úspěšně, v době spuštění a nikdy ztrátě dat se vám účtovat. Mezi příklady patří `Single` k `Double`, `Char` k `String`a na jeho základní typ odvozený typ. Tento poslední převod je rozšíření, protože odvozený typ obsahuje všechny členy ze základního typu a tedy instanci základního typu.  
  
 Není nutné používat časově náročný kód `CType` pro rozšiřující převody, i když `Option Strict` je `On`.  
  
 `Widening` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Příklad naleznete v tématu definice rozšíření a zúžení operátory převodu [jak: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Postupy: Definice operátora převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
