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
ms.openlocfilehash: f7724053e3732c909523e4e2d3b65bb1918c29d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362356"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Označuje, že operátor převodu ( `CType` ) převede třídu nebo strukturu na typ, který nemusí být schopný uchovat některé z možných hodnot původní třídy nebo struktury.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Převod s klíčovým slovem zúžení  
 Postup převodu musí být `Public Shared` kromě `Narrowing` .  
  
 Zužující převody nejsou vždycky úspěšné v době běhu a můžou selhat nebo může dojít ke ztrátě dat. Příklady jsou `Long` `Integer` , `String` do a `Date` základní typ pro odvozený typ. Tento poslední převod je zúžený, protože základní typ nemusí obsahovat všechny členy odvozeného typu, a proto není instancí odvozeného typu.  
  
 V takovém případě `Option Strict` `On` musí kód náročné použít `CType` pro všechny zužující převody.  
  
 `Narrowing`Klíčové slovo lze použít v tomto kontextu:  
  
 [Operator – příkaz](../statements/operator-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Operator – příkaz](../statements/operator-statement.md)
- [Rozšíření](widening.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Postupy: Definice operátoru](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType – funkce](../functions/ctype-function.md)
- [Option Strict – příkaz](../statements/option-strict-statement.md)
