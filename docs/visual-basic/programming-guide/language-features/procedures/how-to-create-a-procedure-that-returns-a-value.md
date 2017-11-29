---
title: "Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).
Můžete použít `Function` postup vrátit hodnotu volání kódu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>K vytvoření procedury, která vrátí hodnotu  
  
1.  Mimo jiné postup použijte `Function` prohlášení, za nímž následuje `End Function` příkaz.  
  
2.  V `Function` prohlášení, postupujte podle `Function` – klíčové slovo s názvem postupu a seznam parametrů v závorkách.  
  
3.  Postupujte podle závorkách s `As` klauzule zadat datový typ vrácené hodnoty.  
  
4.  Umístit postup kód příkazy mezi `Function` a `End Function` příkazy.  
  
5.  Použití `Return` příkaz k vrácení hodnoty volání kódu.  
  
     Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku vpravo, pro zbývající dvě strany zadané hodnoty.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Postupy: vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Postupy: volání procedury, která vrátí hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
