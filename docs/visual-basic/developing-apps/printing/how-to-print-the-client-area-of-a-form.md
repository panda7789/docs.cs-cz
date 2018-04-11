---
title: 'Postupy: Tisk klientské oblasti formuláře (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="78c2e-102">Postupy: Tisk klientské oblasti formuláře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78c2e-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="78c2e-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, bez použití <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="78c2e-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="78c2e-104">Následující postup ukazuje, jak tisk právě klientské oblasti formuláře, bez záhlaví, ohraničení a posuvníky.</span><span class="sxs-lookup"><span data-stu-id="78c2e-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="78c2e-105">Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="78c2e-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="78c2e-106">Tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="78c2e-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="78c2e-107">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="78c2e-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="78c2e-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.</span><span class="sxs-lookup"><span data-stu-id="78c2e-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="78c2e-109">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="78c2e-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="78c2e-110">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).</span><span class="sxs-lookup"><span data-stu-id="78c2e-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="78c2e-111">V některých operačních systémů, text nebo grafické vykresleny podle <xref:System.Drawing.Graphics> metody nestiskne správně.</span><span class="sxs-lookup"><span data-stu-id="78c2e-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="78c2e-112">V takovém případě použijte kompatibilní tisk metodu: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="78c2e-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c2e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="78c2e-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="78c2e-114">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="78c2e-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="78c2e-115">Postupy: Tisk klientských i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="78c2e-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="78c2e-116">Postupy: Tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="78c2e-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
