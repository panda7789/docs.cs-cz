---
title: 'Postupy: Provádění operací přetažení myší mezi aplikacemi'
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
ms.openlocfilehash: 1e9556a69f3f5da4a47c5f5b1a6043a9a73dd8ff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713433"
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a><span data-ttu-id="ec99a-102">Postupy: Provádění operací přetažení myší mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="ec99a-102">How to: Perform Drag-and-Drop Operations Between Applications</span></span>
<span data-ttu-id="ec99a-103">Provádění operací přetažení myší mezi aplikacemi se nijak neliší od povolení této akce v rámci aplikace, tak dlouho, dokud zahrnuté obě aplikace chovat podle "smlouva" mezi <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> a <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ec99a-103">Performing drag-and-drop operations between applications is no different than enabling this action within an application, as long as both applications involved behave according to the "contract" established between the <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> and <xref:System.Windows.Forms.DragEventArgs.Effect%2A> properties.</span></span>  
  
 <span data-ttu-id="ec99a-104">V následujícím postupu budete používat aplikace založené na Windows, které vytvoříte a WordPad textový procesor, který je součástí operačního systému Windows k provádění operací přetažení myší mezi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="ec99a-104">In the following procedure, you will use a Windows-based application you create and the WordPad word processor that is included with the Windows operating system to perform drag-and-drop operations between applications.</span></span> <span data-ttu-id="ec99a-105">WordPad má určitou sadu povolené efekty text, který je přetáhnout; aplikace založené na Windows, které budete psát kód pro spolupráci s negativních dopadů tak, aby se může úspěšně dokončit operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ec99a-105">WordPad has a certain set of allowed effects for text being dragged and dropped; the Windows-based application you will write code for will work with these effects so that drag-and-drop operations may be completed successfully.</span></span>  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a><span data-ttu-id="ec99a-106">Postup a přetažení mezi aplikacemi</span><span class="sxs-lookup"><span data-stu-id="ec99a-106">To perform a drag-and-drop procedure between applications</span></span>  
  
1.  <span data-ttu-id="ec99a-107">Vytvoření nové aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ec99a-107">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="ec99a-108">Přidat <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ec99a-108">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
3.  <span data-ttu-id="ec99a-109">Konfigurace <xref:System.Windows.Forms.TextBox> ovládací prvek přijímat vynechaných data.</span><span class="sxs-lookup"><span data-stu-id="ec99a-109">Configure the <xref:System.Windows.Forms.TextBox> control to receive dropped data.</span></span>  
  
     <span data-ttu-id="ec99a-110">Další informace najdete v tématu [názorný postup: Operace a přetažení ve Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ec99a-110">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
4.  <span data-ttu-id="ec99a-111">Spuštění aplikace založené na Windows a když je spuštěná aplikace, spustit program WordPad.</span><span class="sxs-lookup"><span data-stu-id="ec99a-111">Run your Windows-based application, and while the application is running, run WordPad.</span></span>  
  
     <span data-ttu-id="ec99a-112">WordPad je textový editor a nainstalované ve Windows, který umožňuje operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="ec99a-112">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="ec99a-113">Stisknutím kombinace kláves je přístupný **Start** tlačítka, výběr **spustit**a zadáním `WordPad` do textového pole **spustit** dialogové okno a kliknutím na **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec99a-113">It is accessible by pressing the **Start** button, selecting **Run**, and then typing `WordPad` into the text box of the **Run** dialog box and clicking **OK**.</span></span>  
  
5.  <span data-ttu-id="ec99a-114">Jakmile WordPad otevře, zadejte do něj textového řetězce.</span><span class="sxs-lookup"><span data-stu-id="ec99a-114">Once WordPad is open, type a string of text into it.</span></span>  
  
6.  <span data-ttu-id="ec99a-115">Pomocí myši, vyberte text a pak přetáhněte vybraný text na <xref:System.Windows.Forms.TextBox> ovládacího prvku v aplikaci založené na Windows.</span><span class="sxs-lookup"><span data-stu-id="ec99a-115">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.TextBox> control in your Windows-based application.</span></span>  
  
     <span data-ttu-id="ec99a-116">Pozorujte, že když najedete myší <xref:System.Windows.Forms.TextBox> ovládacího prvku (a v důsledku toho vyvolat <xref:System.Windows.Forms.Control.DragEnter> událostí), změní se kurzor který lze přetáhnout vybraný text do <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ec99a-116">Observe that when you mouse over the <xref:System.Windows.Forms.TextBox> control (and, consequently, raise the <xref:System.Windows.Forms.Control.DragEnter> event), the cursor changes, and you can drop the selected text into the <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
     <span data-ttu-id="ec99a-117">Kromě toho můžete nakonfigurovat váš <xref:System.Windows.Forms.TextBox> ovládací prvek umožňující textových řetězců, které se přetáhnout do WordPad.</span><span class="sxs-lookup"><span data-stu-id="ec99a-117">Additionally, you can configure your <xref:System.Windows.Forms.TextBox> control to allow text strings to be dragged and dropped into WordPad.</span></span> <span data-ttu-id="ec99a-118">Další informace najdete v tématu [názorný postup: Operace a přetažení ve Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ec99a-118">For more information, see [Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec99a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec99a-119">See also</span></span>
- [<span data-ttu-id="ec99a-120">Postupy: Přidání dat do schránky.</span><span class="sxs-lookup"><span data-stu-id="ec99a-120">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
- [<span data-ttu-id="ec99a-121">Postupy: Načtení dat ze schránky</span><span class="sxs-lookup"><span data-stu-id="ec99a-121">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
- [<span data-ttu-id="ec99a-122">Operace přetažení a podpora schránky</span><span class="sxs-lookup"><span data-stu-id="ec99a-122">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
