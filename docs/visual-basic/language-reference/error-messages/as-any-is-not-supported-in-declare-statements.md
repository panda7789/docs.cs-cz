---
title: '&#39;Jako některý&#39; nepodporuje &#39;Declare&#39; příkazy'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 560ddc8674718f98f3e1a2f6d4facdb198f5e506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709856"
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="f76bc-102">&#39;Jako některý&#39; nepodporuje &#39;Declare&#39; příkazy</span><span class="sxs-lookup"><span data-stu-id="f76bc-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="f76bc-103">`Any` Datový typ byl použit s `Declare` příkazy ve Visual Basicu 6.0 a starší verze, tak, aby povolovala použití argumentů, které by mohly obsahovat jakýkoli typ dat.</span><span class="sxs-lookup"><span data-stu-id="f76bc-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="f76bc-104">Přetížení, ale podporuje jazyka Visual Basic a tak provede `Any` datového typu zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f76bc-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="f76bc-105">**ID chyby:** BC30828</span><span class="sxs-lookup"><span data-stu-id="f76bc-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f76bc-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f76bc-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f76bc-107">Deklarovat parametry konkrétní typ, který chcete použít; např.</span><span class="sxs-lookup"><span data-stu-id="f76bc-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="f76bc-108">Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy `As Any` při `Void*` datacommand procedura volána.</span><span class="sxs-lookup"><span data-stu-id="f76bc-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f76bc-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f76bc-109">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f76bc-110">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="f76bc-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="f76bc-111">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="f76bc-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="f76bc-112">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="f76bc-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
