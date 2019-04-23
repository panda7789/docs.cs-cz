---
title: Výraz 'As Any' již není podporován v příkazech 'Declare'.
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310691"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a><span data-ttu-id="622e2-102">Výraz 'As Any' již není podporován v příkazech 'Declare'.</span><span class="sxs-lookup"><span data-stu-id="622e2-102">'As Any' is not supported in 'Declare' statements</span></span>
<span data-ttu-id="622e2-103">`Any` Datový typ byl použit s `Declare` příkazy ve Visual Basicu 6.0 a starší verze, tak, aby povolovala použití argumentů, které by mohly obsahovat jakýkoli typ dat.</span><span class="sxs-lookup"><span data-stu-id="622e2-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="622e2-104">Přetížení, ale podporuje jazyka Visual Basic a tak provede `Any` datového typu zastaralá.</span><span class="sxs-lookup"><span data-stu-id="622e2-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="622e2-105">**ID chyby:** BC30828</span><span class="sxs-lookup"><span data-stu-id="622e2-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="622e2-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="622e2-106">To correct this error</span></span>  
  
1. <span data-ttu-id="622e2-107">Deklarovat parametry konkrétní typ, který chcete použít; např.</span><span class="sxs-lookup"><span data-stu-id="622e2-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. <span data-ttu-id="622e2-108">Použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributy `As Any` při `Void*` datacommand procedura volána.</span><span class="sxs-lookup"><span data-stu-id="622e2-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a><span data-ttu-id="622e2-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="622e2-109">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="622e2-110">Návod: Volání rozhraní API systému Windows</span><span class="sxs-lookup"><span data-stu-id="622e2-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="622e2-111">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="622e2-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="622e2-112">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="622e2-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
