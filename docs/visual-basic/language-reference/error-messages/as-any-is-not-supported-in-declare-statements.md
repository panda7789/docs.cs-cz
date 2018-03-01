---
title: "& č. 39; Jako žádné & č. 39; není podporována v & č. 39; Declare & č. 39; příkazy"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="7bcd4-102">& č. 39; Jako žádné & č. 39; není podporována v & č. 39; Declare & č. 39; příkazy</span><span class="sxs-lookup"><span data-stu-id="7bcd4-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="7bcd4-103">`Any` Datový typ se použila se `Declare` příkazy v Visual Basic 6.0 a starší verze, které chcete povolit použití argumenty, které může obsahovat jakýkoli typ dat.</span><span class="sxs-lookup"><span data-stu-id="7bcd4-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="7bcd4-104">podporuje přetížení, ale a díky tomu tak `Any` datový typ zastaralé.</span><span class="sxs-lookup"><span data-stu-id="7bcd4-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="7bcd4-105">**ID chyby:** BC30828</span><span class="sxs-lookup"><span data-stu-id="7bcd4-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7bcd4-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7bcd4-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7bcd4-107">Deklarovat parametry specifický typ, který chcete použít; například.</span><span class="sxs-lookup"><span data-stu-id="7bcd4-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="7bcd4-108">Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut k určení `As Any` při `Void*` je očekáváno procedura volaná.</span><span class="sxs-lookup"><span data-stu-id="7bcd4-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7bcd4-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bcd4-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="7bcd4-110">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="7bcd4-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="7bcd4-111">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="7bcd4-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="7bcd4-112">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="7bcd4-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
