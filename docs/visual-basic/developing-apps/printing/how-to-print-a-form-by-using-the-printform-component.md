---
title: "Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5edad4f04b98dcf0dfa328f111db5dcb423036e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="99338-102">Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99338-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="99338-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Součást umožňuje rychle tisk obrázku ve tvaru, který přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> součásti.</span><span class="sxs-lookup"><span data-stu-id="99338-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="99338-104">Následující postupy ukazují, jak tisk formuláře k tiskárně, okno náhledu tisku a do souboru Encapsulated PostScript.</span><span class="sxs-lookup"><span data-stu-id="99338-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="99338-105">Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="99338-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="99338-106">Tisk formuláře do výchozí tiskárny</span><span class="sxs-lookup"><span data-stu-id="99338-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="99338-107">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="99338-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="99338-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.</span><span class="sxs-lookup"><span data-stu-id="99338-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="99338-109">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="99338-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="99338-110">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).</span><span class="sxs-lookup"><span data-stu-id="99338-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="99338-111">K zobrazení formuláře v okně náhledu tisku</span><span class="sxs-lookup"><span data-stu-id="99338-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="99338-112">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="99338-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="99338-113"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.</span><span class="sxs-lookup"><span data-stu-id="99338-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="99338-114">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="99338-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="99338-115">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).</span><span class="sxs-lookup"><span data-stu-id="99338-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="99338-116">Tisk formuláře do souboru</span><span class="sxs-lookup"><span data-stu-id="99338-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="99338-117">V **sada nástrojů**, klikněte na tlačítko **PowerPacks jazyka Visual Basic** kartě a poté přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="99338-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="99338-118"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do komponent.</span><span class="sxs-lookup"><span data-stu-id="99338-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="99338-119">V **vlastnosti** nastavte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="99338-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="99338-120">Volitelně vyberte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost a zadejte Úplná cesta a název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="99338-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="99338-121">Pokud tento krok přeskočíte, uživateli zobrazí výzva k zadání názvu souboru v době běhu.</span><span class="sxs-lookup"><span data-stu-id="99338-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="99338-122">Přidejte následující kód v obslužné rutině příslušné události (například v `Click` obslužné rutiny události pro **tiskových**`Button`).</span><span class="sxs-lookup"><span data-stu-id="99338-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99338-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="99338-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [<span data-ttu-id="99338-124">Postupy: tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="99338-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="99338-125">Postupy: tisk klientských i Neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="99338-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="99338-126">Postupy: tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="99338-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [<span data-ttu-id="99338-127">PrintForm – součást</span><span class="sxs-lookup"><span data-stu-id="99338-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
