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
ms.openlocfilehash: e30f4b21d8b8f1a4c5a168402ce5cc386d932f86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510608"
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="892e0-102">ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="892e0-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="892e0-103">Windows Forms `ListView` ovládací prvek zobrazuje seznam položek s ikonami.</span><span class="sxs-lookup"><span data-stu-id="892e0-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="892e0-104">Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je pravém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="892e0-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="892e0-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="892e0-105">In This Section</span></span>  
 [<span data-ttu-id="892e0-106">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="892e0-107">Popisuje tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="892e0-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="892e0-108">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-109">Popisuje, jak přidat nebo odebrat položky ze zobrazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="892e0-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="892e0-110">Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-111">Popisuje, jak vytvořit sloupce k zobrazení informací o každou položku seznamu.</span><span class="sxs-lookup"><span data-stu-id="892e0-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="892e0-112">Postupy: Zobrazení ikon pro ovládací prvek Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-113">Popisuje postup zobrazení seznamu přidružení seznamu obrázků vhodné pro velké nebo malé ikony zobrazení.</span><span class="sxs-lookup"><span data-stu-id="892e0-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="892e0-114">Postupy: Zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-115">Popisuje, jak zobrazit informace o jednotlivých položkách seznamu sloupců.</span><span class="sxs-lookup"><span data-stu-id="892e0-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="892e0-116">Postupy: Výběr položky v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-117">Popisuje, jak prostřednictvím kódu programu vyberte nějakou položku.</span><span class="sxs-lookup"><span data-stu-id="892e0-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="892e0-118">Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-119">Popisuje, jak vytvořit skupiny pro zobrazení podle kategorií a přiřazení položky pro každou skupinu.</span><span class="sxs-lookup"><span data-stu-id="892e0-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="892e0-120">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="892e0-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="892e0-121">Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-122">Popisuje, jak zobrazit položky jako dlaždice, z nichž každý je tvořený velké ikony a více řádků textu.</span><span class="sxs-lookup"><span data-stu-id="892e0-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="892e0-123">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="892e0-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="892e0-124">Postupy: Zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="892e0-125">Popisuje, jak implementovat zpětné vazby uživatelů pro operace přetažení myší, ve kterých značky vložení označuje umístění přetažení pro každou pozici ukazatele myši.</span><span class="sxs-lookup"><span data-stu-id="892e0-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="892e0-126">Tato funkce je dostupná jenom pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="892e0-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="892e0-127">Postupy: Přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="892e0-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="892e0-128">Popisuje, jak prostřednictvím kódu programu najít pomocí vyhledávání nebo obrazovku souřadnic buď textu položky.</span><span class="sxs-lookup"><span data-stu-id="892e0-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   [<span data-ttu-id="892e0-129">Postupy: Povolení zobrazení Vedle sebe v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="892e0-129">How to: Enable Tile View in a Windows Forms ListView Control Using the Designer</span></span>](enable-tile-view-in-a-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="892e0-130">Postupy: Přidávání a odebírání položek pomocí ovládacího prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="892e0-130">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>](add-and-remove-items-with-wf-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="892e0-131">Postupy: Přidávání sloupců do ovládacího prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="892e0-131">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>](how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="892e0-132">Postupy: Seskupování položek v ovládacím prvku Windows Forms ListView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="892e0-132">How to: Group Items in a Windows Forms ListView Control Using the Designer</span></span>](how-to-group-items-in-a-windows-forms-listview-control-using-the-designer.md)  
  
-   [<span data-ttu-id="892e0-133">Návod: Vytváření rozhraní ve stylu Průzkumníka s ovládacími prvky ListView a TreeView pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="892e0-133">Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer</span></span>](creating-an-explorer-style-interface-with-the-listview-and-treeview.md)  
  
## <a name="reference"></a><span data-ttu-id="892e0-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="892e0-134">Reference</span></span>  
 <span data-ttu-id="892e0-135"><xref:System.Windows.Forms.ListView> Třída</span><span class="sxs-lookup"><span data-stu-id="892e0-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="892e0-136">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="892e0-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="892e0-137">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="892e0-137">Related Sections</span></span>  
 [<span data-ttu-id="892e0-138">Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="892e0-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="892e0-139">Popisuje, jak dědit z nebo položky v zobrazení seznamu uzlu ve stromovém zobrazení, chcete-li přidat libovolné pole, metody nebo konstruktory, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="892e0-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="892e0-140">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="892e0-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="892e0-141">Vysvětluje, jaké seznamu obrázků je a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="892e0-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="892e0-142">Postupy: Vytváření uživatelského rozhraní s více podokny pomocí Windows Forms</span><span class="sxs-lookup"><span data-stu-id="892e0-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="892e0-143">Poskytuje pokyny pro vytváření rozložení formuláře Windows s více podokny.</span><span class="sxs-lookup"><span data-stu-id="892e0-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="892e0-144">Funkce Windows XP a ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="892e0-144">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="892e0-145">Vysvětluje, jak využít výhod funkce specifické pro Windows XP, které se vztahují <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="892e0-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="892e0-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="892e0-146">See Also</span></span>  
 [<span data-ttu-id="892e0-147">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="892e0-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
