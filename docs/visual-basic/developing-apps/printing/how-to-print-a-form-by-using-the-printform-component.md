---
title: 'Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 723524c7c9876d353624ad47d504ea2528a31cfe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422724"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="3b8d0-102">Postupy: Tisk formuláře pomocí součásti PrintForm (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b8d0-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="3b8d0-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Komponenty umožňuje rychlý tisk obrázek formuláře přesně tak, jak se zobrazí na obrazovce bez použití <xref:System.Drawing.Printing.PrintDocument> komponenty.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="3b8d0-104">Následující postupy ukazují, jak tisk formuláře tiskárny, okno náhledu tisku a soubor zapouzdřené PostScript.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="3b8d0-105">Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="3b8d0-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="3b8d0-106">Tisk formuláře, použije se výchozí tiskárna</span><span class="sxs-lookup"><span data-stu-id="3b8d0-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="3b8d0-107">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3b8d0-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3b8d0-109">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="3b8d0-110">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3b8d0-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="3b8d0-111">K zobrazení formuláře v okně Náhled tisku</span><span class="sxs-lookup"><span data-stu-id="3b8d0-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="3b8d0-112">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3b8d0-113"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3b8d0-114">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="3b8d0-115">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3b8d0-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="3b8d0-116">Tisk formuláře do souboru</span><span class="sxs-lookup"><span data-stu-id="3b8d0-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="3b8d0-117">V **nástrojů**, klikněte na tlačítko **sady Visual Basic PowerPack** kartu a potom přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="3b8d0-118"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Přidání komponenty do panelu komponent.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="3b8d0-119">V **vlastnosti** okno, nastaveno <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> vlastnost <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="3b8d0-120">Volitelně můžete vybrat <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> vlastnost a zadejte úplnou cestu a název souboru název cílového souboru.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="3b8d0-121">Pokud tento krok přeskočíte, uživateli zobrazí výzva k zadání názvu souboru v době běhu.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="3b8d0-122">Přidejte následující kód v obslužné rutině události (například v `Click` obslužné rutiny událostí pro **tisk**`Button`).</span><span class="sxs-lookup"><span data-stu-id="3b8d0-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3b8d0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b8d0-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [<span data-ttu-id="3b8d0-124">Postupy: Tisk klientské oblasti formuláře</span><span class="sxs-lookup"><span data-stu-id="3b8d0-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="3b8d0-125">Postupy: Tisk klientských i neklientských oblastí formuláře</span><span class="sxs-lookup"><span data-stu-id="3b8d0-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="3b8d0-126">Postupy: Tisk posuvného formuláře</span><span class="sxs-lookup"><span data-stu-id="3b8d0-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [<span data-ttu-id="3b8d0-127">Komponenta PrintForm</span><span class="sxs-lookup"><span data-stu-id="3b8d0-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
