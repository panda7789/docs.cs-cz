---
title: Rozšíření
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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359900"
---
# <a name="widening-visual-basic"></a>Rozšíření (Visual Basic)
Označuje, že operátor převodu ( `CType` ) převede třídu nebo strukturu na typ, který může uchovávat všechny možné hodnoty původní třídy nebo struktury.  
  
## <a name="converting-with-the-widening-keyword"></a>Převod pomocí klíčového slova rozšiřování  
 Postup převodu musí být `Public Shared` kromě `Widening` .  
  
 Rozšiřující převody jsou vždy úspěšné v době běhu a nikdy neúčtují ztrátu dat. Příklady jsou `Single` `Double` , `Char` do a `String` odvozeného typu na jeho základní typ. Tento poslední převod se rozšiřuje, protože odvozený typ obsahuje všechny členy základního typu, a proto je instancí základního typu.  
  
 Nenáročný kód nemusí být použit `CType` pro rozšiřující převody, a to ani v případě, že `Option Strict` je `On` .  
  
 `Widening`Klíčové slovo lze použít v tomto kontextu:  
  
 [Operator – příkaz](../statements/operator-statement.md)  
  
 Například definice rozšiřujících a zužujících operátorů převodu naleznete v tématu [How to: define a Conversion](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)operator.  
  
## <a name="see-also"></a>Viz také

- [Operator – příkaz](../statements/operator-statement.md)
- [Narrowing](narrowing.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType – funkce](../functions/ctype-function.md)
- [Option Strict – příkaz](../statements/option-strict-statement.md)
- [Postupy: Definice operátoru převodu](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
