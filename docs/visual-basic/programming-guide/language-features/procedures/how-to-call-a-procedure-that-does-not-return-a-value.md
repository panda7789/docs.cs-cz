---
title: 'Postupy: Volání procedury, která nevrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 6e3ce2a184ca5411a6a016929a16bf3d67e669ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335469"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="c1032-102">Postupy: Volání procedury, která nevrací hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1032-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="c1032-103">A `Sub` procedury nesmí vracet hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="c1032-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="c1032-104">Zavoláte ji explicitně pomocí samostatné volání příkazu.</span><span class="sxs-lookup"><span data-stu-id="c1032-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="c1032-105">Nelze volat ho jednoduše pomocí jeho názvu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="c1032-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="c1032-106">Chcete-li volat proceduru Sub</span><span class="sxs-lookup"><span data-stu-id="c1032-106">To call a Sub procedure</span></span>  
  
1. <span data-ttu-id="c1032-107">Zadejte název `Sub` postup.</span><span class="sxs-lookup"><span data-stu-id="c1032-107">Specify the name of the `Sub` procedure.</span></span>  
  
2. <span data-ttu-id="c1032-108">Použijte název procedury se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="c1032-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c1032-109">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="c1032-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="c1032-110">Však pomocí závorek díky váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="c1032-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="c1032-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="c1032-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c1032-112">Je nutné zadat argumenty ve stejném pořadí, které `Sub` procedura definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="c1032-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="c1032-113">Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkce k aktivaci okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="c1032-113">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="c1032-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> Titulek okna přijímá jako její jediný argument.</span><span class="sxs-lookup"><span data-stu-id="c1032-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="c1032-115">Nevrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="c1032-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="c1032-116">Pokud není spuštěný proces Poznámkový blok, příklad vyvolá <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c1032-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="c1032-117">`Shell` Postup předpokládá, že jsou aplikace v zadaných cest.</span><span class="sxs-lookup"><span data-stu-id="c1032-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="c1032-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1032-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [<span data-ttu-id="c1032-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="c1032-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c1032-120">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="c1032-120">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="c1032-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="c1032-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c1032-122">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="c1032-122">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c1032-123">Postupy: Vytvoření procedury</span><span class="sxs-lookup"><span data-stu-id="c1032-123">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)
- [<span data-ttu-id="c1032-124">Postupy: Volání procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="c1032-124">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="c1032-125">Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c1032-125">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
