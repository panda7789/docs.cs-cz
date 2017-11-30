---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Určuje, že operátora převodu (`CType`) převede třídu nebo strukturu na typ, který nemusí obsahovat některé možné hodnoty z původní třídu nebo strukturu.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Převádění s Narrowing – klíčové slovo  
 Musíte zadat procesu převodu `Public Shared` kromě `Narrowing`.  
  
 Zužující převody není vždy úspěch v době běhu a může selhat nebo dojít ke ztrátě dat. Příklady `Long` k `Integer`, `String` k `Date`a základní typ pro odvozený typ. Tento poslední převod je zužující, protože základní typ nemusí obsahovat všechny členy odvozený typ a proto není instance odvozeného typu.  
  
 Pokud `Option Strict` je `On`, využívání kód musíte použít `CType` pro všechny zužující převody.  
  
 `Narrowing` – Klíčové slovo lze použít v tomto kontextu:  
  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Operator – příkaz](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Rozšíření](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Postupy: definice operátora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)
