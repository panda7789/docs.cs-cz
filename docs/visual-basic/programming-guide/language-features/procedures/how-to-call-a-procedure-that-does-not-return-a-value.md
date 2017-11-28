---
title: "Postupy: Volání procedury, která nevrátí hodnotu (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="05323-102">Postupy: Volání procedury, která nevrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="05323-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="05323-103">A `Sub` postup nevrátí hodnotu kód volání.</span><span class="sxs-lookup"><span data-stu-id="05323-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="05323-104">Zavoláte ji explicitně příkazem samostatné volání.</span><span class="sxs-lookup"><span data-stu-id="05323-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="05323-105">Nelze volat ho jednoduše pomocí jeho názvu v rámci výrazu.</span><span class="sxs-lookup"><span data-stu-id="05323-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="05323-106">K volání Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="05323-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="05323-107">Zadejte název `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="05323-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="05323-108">Použijte název procedury v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="05323-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="05323-109">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="05323-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="05323-110">Však pomocí závorek usnadňuje kódu čtení.</span><span class="sxs-lookup"><span data-stu-id="05323-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="05323-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="05323-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="05323-112">Ujistěte se, zadejte argumenty ve stejném pořadí, `Sub` postupu definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="05323-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="05323-113">Následující příklad volání [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkce aktivovat okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="05323-113">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="05323-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>vezme jako jeho jedinou argument záhlaví okna.</span><span class="sxs-lookup"><span data-stu-id="05323-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="05323-115">Volání kódu nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="05323-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="05323-116">Pokud není spuštěn proces poznámkového bloku, v příkladu vyvolá <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="05323-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="05323-117">`Shell` Postup předpokládá, že se aplikace v zadané cesty.</span><span class="sxs-lookup"><span data-stu-id="05323-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="05323-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="05323-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [<span data-ttu-id="05323-119">Postupy</span><span class="sxs-lookup"><span data-stu-id="05323-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="05323-120">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="05323-120">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="05323-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="05323-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="05323-122">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="05323-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="05323-123">Postupy: vytvoření procedury</span><span class="sxs-lookup"><span data-stu-id="05323-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="05323-124">Postupy: volání procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="05323-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="05323-125">Postupy: volání obslužné rutiny událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05323-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
