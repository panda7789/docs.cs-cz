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
ms.openlocfilehash: 566cf295462945a6bc90bc96f8907de34646bd00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584739"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="99003-102">Postupy: Tisk klientských a neklientských oblastí formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99003-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="99003-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, který přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="99003-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="99003-104">Následující postup ukazuje, jak tisk formuláře, včetně klientské oblasti a neklientská oblast.</span><span class="sxs-lookup"><span data-stu-id="99003-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="99003-105">Neklientská oblast zahrnuje záhlaví, ohraničení a posuňte řádky.</span><span class="sxs-lookup"><span data-stu-id="99003-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="99003-106">Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="99003-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="99003-107">Tisknout klientovi i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="99003-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="99003-108">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="99003-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="99003-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.</span><span class="sxs-lookup"><span data-stu-id="99003-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="99003-110">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="99003-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="99003-111">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro tisku `Button`).</span><span class="sxs-lookup"><span data-stu-id="99003-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="99003-112">V některých operačních systémů, text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="99003-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="99003-113">In this Case, použijte metodu kompatibilní tisk: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="99003-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99003-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="99003-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="99003-115">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="99003-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="99003-116">Postupy: Tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="99003-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
