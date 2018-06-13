---
title: 'Postupy: Tisk posuvného formuláře (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: d43c2e0e564f6f0c37831cd3105a16c4bc4aaea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584011"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="00d98-102">Postupy: Tisk posuvného formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d98-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="00d98-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, bez použití <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="00d98-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="00d98-104">Ve výchozím nastavení je aktuálně viditelné části formuláře vytištěno; Pokud uživatel má ke změně velikosti formuláře za běhu, bitovou kopii nestiskne tak, jak má.</span><span class="sxs-lookup"><span data-stu-id="00d98-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="00d98-105">Následující postup ukazuje, jak tisk posuvného formuláře, v oblasti úplnou klienta i v případě, že velikost formuláře byla změněna.</span><span class="sxs-lookup"><span data-stu-id="00d98-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="00d98-106">Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="00d98-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="00d98-107">Tisk posuvného formuláře v oblasti úplnou klienta</span><span class="sxs-lookup"><span data-stu-id="00d98-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="00d98-108">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="00d98-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="00d98-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást budou přidány do komponent.</span><span class="sxs-lookup"><span data-stu-id="00d98-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="00d98-110">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="00d98-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="00d98-111">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).</span><span class="sxs-lookup"><span data-stu-id="00d98-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="00d98-112">V některých operačních systémů, text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="00d98-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="00d98-113">V takovém případě nebudete moct tisknout se `Scrollable` parametr.</span><span class="sxs-lookup"><span data-stu-id="00d98-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d98-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d98-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="00d98-115">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="00d98-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="00d98-116">Postupy: Tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="00d98-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="00d98-117">Postupy: Tisk klientských i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="00d98-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
