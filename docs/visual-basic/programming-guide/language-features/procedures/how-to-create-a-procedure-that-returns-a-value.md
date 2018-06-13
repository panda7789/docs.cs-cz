---
title: 'Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 472f55173a4897a23a82812a2b24bf1646c1a6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648434"
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
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)  
 [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
