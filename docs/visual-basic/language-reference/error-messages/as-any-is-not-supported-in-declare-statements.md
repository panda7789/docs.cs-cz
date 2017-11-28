---
title: "& č. 39; Jako žádné & č. 39; není podporována v & č. 39; Declare & č. 39; příkazy"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords: BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a>& č. 39; Jako žádné & č. 39; není podporována v & č. 39; Declare & č. 39; příkazy
`Any` Datový typ se použila se `Declare` příkazy v Visual Basic 6.0 a starší verze, které chcete povolit použití argumenty, které může obsahovat jakýkoli typ dat. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]podporuje přetížení, ale a díky tomu tak `Any` datový typ zastaralé.  
  
 **ID chyby:** BC30828  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Deklarovat parametry specifický typ, který chcete použít; například.  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k určení `As Any` při `Void*` je očekáváno procedura volaná.  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Návod: Volání rozhraní API systému Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Vytváření prototypů ve spravovaném kódu](../../../framework/interop/creating-prototypes-in-managed-code.md)
