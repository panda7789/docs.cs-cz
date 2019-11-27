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
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347835"
---
# <a name="widening-visual-basic"></a>Rozšíření (Visual Basic)
Označuje, že operátor převodu (`CType`) převede třídu nebo strukturu na typ, který může uchovávat všechny možné hodnoty původní třídy nebo struktury.  
  
## <a name="converting-with-the-widening-keyword"></a>Převod pomocí klíčového slova rozšiřování  
 Postup převodu musí kromě `Widening`zadat `Public Shared`.  
  
 Rozšiřující převody jsou vždy úspěšné v době běhu a nikdy neúčtují ztrátu dat. Příklady jsou `Single` `Double`, `Char` na `String`a odvozeného typu na jeho základní typ. Tento poslední převod se rozšiřuje, protože odvozený typ obsahuje všechny členy základního typu, a proto je instancí základního typu.  
  
 Nenáročný kód nemusí používat `CType` pro rozšiřující převody, a to i v případě, že `Option Strict` je `On`.  
  
 Klíčové slovo `Widening` lze použít v tomto kontextu:  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Například definice rozšiřujících a zužujících operátorů převodu naleznete v tématu [How to: define a Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)operator.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
