---
title: "Postupy: Volání přetížené procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff5967c1b09ad59f249297b1cf0a4ed900faf4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Postupy: Volání přetížené procedury (Visual Basic)
Výhodou přetížení procedury je v flexibilitu volání. Volání kódu můžete získat informace, které je nutné předat postupu a pak zavolají název jedinou proceduru, bez ohledu na to, jaké argumentů je předávání.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>K volání procedury, která má definovaný více než jedna verze  
  
1.  Ve volání kódu určují, která data mají být předána do procesu.  
  
2.  Zápis volání procedury běžným způsobem, představuje data v seznamu argumentů. Ujistěte se, že argumenty, které odpovídají seznam parametrů v jednom z verzí definované pro proceduru.  
  
3.  Nemusíte určit, která verze postup volání. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ovládací prvek předává verzi odpovídající vaší seznam argumentů.  
  
     Následující příklad volání `post` postup deklarované v [postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md). Ho získá Identifikace zákazníka, určuje, zda je `String` nebo `Integer`a potom v obou případech zavolá stejným způsobem.  
  
     [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Přetížení procedury](./procedure-overloading.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Postupy: přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)  
 [Přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md)
