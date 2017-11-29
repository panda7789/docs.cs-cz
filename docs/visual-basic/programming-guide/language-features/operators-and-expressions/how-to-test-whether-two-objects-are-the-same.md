---
title: "Postupy: Test, zda jsou dva objekty stejné (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>Postupy: Test, zda jsou dva objekty stejné (Visual Basic).
Pokud máte dvě proměnné, které odkazují na objekty, můžete použít buď `Is` nebo `IsNot` operátor nebo obojí, chcete-li zjistit, zda odkazují na stejnou instanci.  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>K ověření, zda jsou oba objekty stejné  
  
-   Použití [je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) nebo [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) s dvě proměnné, které jako operandy.  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 Můžete chtít určité akci v závislosti na tom, zda dva objekty odkazují na stejnou instanci. Předchozí příklad porovnává `c` proti aktivní ovládací prvek na formuláři `f`. Pokud neexistuje žádné aktivní ovládací prvek, nebo pokud je jedna, ale není na stejnou instanci ovládacího prvku jako `c`, pak se `If` příkaz selže a postup vrátí bez dalšího zpracování.  
  
 Ať už používáte `Is` nebo `IsNot` je řádu osobní užitečný pro vás. Jedním může být snadněji číst než jiné v daném výrazu.  
  
## <a name="see-also"></a>Viz také  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
