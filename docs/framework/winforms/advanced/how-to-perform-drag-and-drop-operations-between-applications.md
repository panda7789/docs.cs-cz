---
title: 'Postupy: Provádění operací přetažení mezi aplikacemi'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 13e884b6afb8fbe7248e59009e89ed749d5727d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525227"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="2cb94-102">Postupy: Provádění operací přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="2cb94-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="2cb94-103">Provádění operací přetažení myší mezi aplikacemi se nejsou jiné než povolíte tuto akci v aplikaci, tak dlouho, dokud obě aplikace související se situací chovat podle "smlouva" navázat mezi <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> a <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2cb94-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="2cb94-104">V následujícím postupu budete používat aplikace pro systém Windows, které vytvoříte a WordPad textový editor, která je součástí operačního systému Windows k provádění operací přetažení myší mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="2cb94-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="2cb94-105">WordPad má určitou sadu povolených důsledky pro text se přetáhnout; aplikace pro systém Windows, které budete psát kód pro bude fungovat s těchto důsledcích tak, aby operací přetažení myší může úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2cb94-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="2cb94-106">Postup a přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="2cb94-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="2cb94-107">Vytvořte novou aplikaci Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2cb94-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="2cb94-108">Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="2cb94-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="2cb94-109">Konfigurace <xref:System.Windows.Forms.TextBox> řízení přijímat vynechaných data.</span><span class="sxs-lookup"><span data-stu-id="2cb94-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="2cb94-110">Další informace najdete v tématu [návod: provádění operace přetažení myší ve Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2cb94-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="2cb94-111">Spusťte aplikaci systému Windows a když aplikace běží, spusťte WordPad.</span><span class="sxs-lookup"><span data-stu-id="2cb94-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="2cb94-112">WordPad je textový editor, nainstalovaná v systému Windows, který umožňuje operací přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="2cb94-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="2cb94-113">Je dostupné po stisknutí **spustit** tlačítko výběru **spustit**a zadáním `WordPad` do textového pole **spustit** dialogové okno a kliknutím na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="2cb94-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="2cb94-114">Jakmile WordPad je otevřený, zadejte řetězec textu do ní.</span><span class="sxs-lookup"><span data-stu-id="2cb94-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="2cb94-115">Pomocí myši, vyberte text a poté přetáhněte vybraný text přes k <xref:System.Windows.Forms.TextBox> ovládací prvek v aplikaci systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2cb94-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="2cb94-116">Všimněte při umístění ukazatele myši <xref:System.Windows.Forms.TextBox> ovládací prvek (a v důsledku toho vyvolat <xref:System.Windows.Forms.Control.DragEnter> událostí), změní a mohou vyřadit vybraný text do <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2cb94-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="2cb94-117">Kromě toho můžete nakonfigurovat vaše <xref:System.Windows.Forms.TextBox> řízení umožňující textové řetězce do přetahování do WordPad.</span><span class="sxs-lookup"><span data-stu-id="2cb94-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="2cb94-118">Další informace najdete v tématu [návod: provádění operace přetažení myší ve Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2cb94-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb94-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cb94-119">See Also</span></span>  
 [<span data-ttu-id="2cb94-120">Postupy: Přidání dat do schránky</span><span class="sxs-lookup"><span data-stu-id="2cb94-120">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [<span data-ttu-id="2cb94-121">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="2cb94-121">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [<span data-ttu-id="2cb94-122">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="2cb94-122">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
