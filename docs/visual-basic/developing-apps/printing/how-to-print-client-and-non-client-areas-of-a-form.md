---
title: 'Postupy: Tisk klientských a neklientských oblastí formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408436"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="68170-102">Postupy: Tisk klientských a neklientských oblastí formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68170-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="68170-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="68170-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="68170-104">Následující postup ukazuje, jak tisk formuláře, včetně klientské oblasti a neklientská oblast.</span><span class="sxs-lookup"><span data-stu-id="68170-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="68170-105">Neklientská oblast obsahuje záhlaví, ohraničení a posuňte pruhy.</span><span class="sxs-lookup"><span data-stu-id="68170-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="68170-106">Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="68170-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="68170-107">Pro tisk klientských i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="68170-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="68170-108">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="68170-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="68170-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="68170-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="68170-110">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="68170-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="68170-111">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny události pro tisku `Button`).</span><span class="sxs-lookup"><span data-stu-id="68170-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="68170-112">V některých operačních systémů, textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="68170-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="68170-113">In this Case, použijte metodu kompatibilní tisku: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="68170-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68170-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="68170-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="68170-115">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="68170-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="68170-116">Postupy: Tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="68170-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
