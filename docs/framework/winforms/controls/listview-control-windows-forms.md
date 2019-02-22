---
title: ListView – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- lists
- checked list items [Windows Forms], Windows Forms controls
- user interface [Windows Forms], creating
- lists [Windows Forms], items with icons
- icons [Windows Forms], listing with items
- list views
- ListView control [Windows Forms]
- list controls [Windows Forms], List view
ms.assetid: 9f71cf5c-82da-488a-a04e-ef52c0817187
ms.openlocfilehash: 207b5fcd8bb1242be180898a22ffacf6e5ac9ab1
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664884"
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="d5ddf-102">ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d5ddf-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="d5ddf-103">Windows Forms `ListView` ovládací prvek zobrazuje seznam položek s ikonami.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="d5ddf-104">Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je pravém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5ddf-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5ddf-105">In This Section</span></span>  
 [<span data-ttu-id="d5ddf-106">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="d5ddf-107">Popisuje tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="d5ddf-108">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-109">Popisuje, jak přidat nebo odebrat položky ze zobrazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="d5ddf-110">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-111">Popisuje, jak vytvořit sloupce k zobrazení informací o každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="d5ddf-112">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-113">Popisuje postup zobrazení seznamu přidružení seznamu obrázků vhodné pro velké nebo malé ikony zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="d5ddf-114">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-115">Popisuje, jak zobrazit informace o jednotlivých položkách seznamu sloupců.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="d5ddf-116">Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-117">Popisuje, jak prostřednictvím kódu programu vyberte nějakou položku.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="d5ddf-118">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-119">Popisuje, jak vytvořit skupiny pro zobrazení podle kategorií a přiřazení položky pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="d5ddf-120">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5ddf-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="d5ddf-121">Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-122">Popisuje, jak zobrazit položky jako dlaždice, z nichž každý je tvořený velké ikony a více řádků textu.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="d5ddf-123">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5ddf-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="d5ddf-124">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="d5ddf-125">Popisuje, jak implementovat zpětné vazby uživatelů pro operace přetažení myší, ve kterých značky vložení označuje umístění přetažení pro každou pozici ukazatele myši.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="d5ddf-126">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5ddf-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="d5ddf-127">Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="d5ddf-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="d5ddf-128">Popisuje, jak prostřednictvím kódu programu najít pomocí vyhledávání nebo obrazovku souřadnic buď textu položky.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   [<span data-ttu-id="d5ddf-129">Postupy: Povolení zobrazení Tile v ovládacím prvku Windows Forms ListView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d5ddf-129">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>](enable-tile-view-in-a-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="d5ddf-130">Postupy: Přidání a odebrání položek s ovládacím prvkem Windows Forms ListView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d5ddf-130">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>](add-and-remove-items-with-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="d5ddf-131">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d5ddf-131">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>](how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="d5ddf-132">Postupy: Seskupení položek v ovládacím prvku Windows Forms ListView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d5ddf-132">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>](how-to-group-items-in-a-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="d5ddf-133">Návod: Vytváření rozhraní ve stylu Průzkumníku s ListView a ovládacích prvků TreeView pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="d5ddf-133">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>](creating-an-explorer-style-interface-with-the-listview-and-treeview.md)  
  
## <a name="reference"></a><span data-ttu-id="d5ddf-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d5ddf-134">Reference</span></span>  
 <span data-ttu-id="d5ddf-135"><xref:System.Windows.Forms.ListView> Třída</span><span class="sxs-lookup"><span data-stu-id="d5ddf-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="d5ddf-136">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d5ddf-137">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d5ddf-137">Related Sections</span></span>  
 [<span data-ttu-id="d5ddf-138">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d5ddf-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="d5ddf-139">Popisuje, jak dědit z nebo položky v zobrazení seznamu uzlu ve stromovém zobrazení, chcete-li přidat libovolné pole, metody nebo konstruktory, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="d5ddf-140">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="d5ddf-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="d5ddf-141">Vysvětluje, jaké seznamu obrázků je a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="d5ddf-142">Postupy: Vytvoření více podokny uživatelského rozhraní pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5ddf-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="d5ddf-143">Poskytuje pokyny pro vytváření rozložení formuláře Windows s více podokny.</span><span class="sxs-lookup"><span data-stu-id="d5ddf-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ddf-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5ddf-144">See also</span></span>
- [<span data-ttu-id="d5ddf-145">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d5ddf-145">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
