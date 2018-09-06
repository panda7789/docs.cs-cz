---
title: 'Postupy: Tisk posuvného formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 4a509b7c48f2bff705bc95e58fb88252cb8ca4b9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779416"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="1bfd2-102">Postupy: Tisk posuvného formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bfd2-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="1bfd2-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="1bfd2-104">Ve výchozím nastavení vytiskne se pouze aktuálně viditelná část formuláře; Pokud uživatel má velikost formuláře v době běhu, nestiskne image tak, jak má.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="1bfd2-105">Následující postup ukazuje, jak vytisknout úplné klientské oblasti posuvného formuláře, i v případě, že se velikost formuláře.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="1bfd2-106">Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="1bfd2-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="1bfd2-107">Chcete-li vytisknout kompletní klientské oblasti posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="1bfd2-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="1bfd2-108">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="1bfd2-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty budou přidány do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="1bfd2-110">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="1bfd2-111">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).</span><span class="sxs-lookup"><span data-stu-id="1bfd2-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1bfd2-112">V některých operačních systémů, textové nebo grafické vykreslené <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="1bfd2-113">V takovém případě nebudete mít k vytištění s `Scrollable` parametru.</span><span class="sxs-lookup"><span data-stu-id="1bfd2-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bfd2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bfd2-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="1bfd2-115">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="1bfd2-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="1bfd2-116">Postupy: Tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="1bfd2-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="1bfd2-117">Postupy: Tisk klientských i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="1bfd2-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
