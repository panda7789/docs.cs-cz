---
title: "ListView – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bdecc3ba33b65b09dd277374b5ea96ce5b0f572e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="listview-control-windows-forms"></a><span data-ttu-id="a11e1-102">ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a11e1-102">ListView Control (Windows Forms)</span></span>
<span data-ttu-id="a11e1-103">Windows Forms `ListView` ovládací prvek zobrazí seznam položky s ikonami.</span><span class="sxs-lookup"><span data-stu-id="a11e1-103">The Windows Forms `ListView` control displays a list of items with icons.</span></span> <span data-ttu-id="a11e1-104">Zobrazení seznamu můžete použít k vytvoření uživatelského rozhraní, jako je v pravém podokně Průzkumníka Windows.</span><span class="sxs-lookup"><span data-stu-id="a11e1-104">You can use a list view to create a user interface like the right pane of Windows Explorer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a11e1-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a11e1-105">In This Section</span></span>  
 [<span data-ttu-id="a11e1-106">Přehled ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="a11e1-106">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 <span data-ttu-id="a11e1-107">Popisuje tento ovládací prvek a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a11e1-107">Describes this control and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a11e1-108">Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-108">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-109">Popisuje postup přidání nebo odebrání položky ze zobrazení seznamu.</span><span class="sxs-lookup"><span data-stu-id="a11e1-109">Describes how to add or remove items from a list view.</span></span>  
  
 [<span data-ttu-id="a11e1-110">Postupy: přidávání sloupců do ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-110">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-111">Popisuje postup vytvoření sloupců, aby bylo možné zobrazit informace o každé položce seznamu.</span><span class="sxs-lookup"><span data-stu-id="a11e1-111">Describes how to create columns in order to display information about each list item.</span></span>  
  
 [<span data-ttu-id="a11e1-112">Postupy: zobrazení ikon pro Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-112">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-113">Popisuje postup zobrazení seznamu přidružit seznamu příslušné bitové kopie pro zobrazení velké nebo malé ikony.</span><span class="sxs-lookup"><span data-stu-id="a11e1-113">Describes how to associate a list view with an appropriate image list for displaying large or small icons.</span></span>  
  
 [<span data-ttu-id="a11e1-114">Postupy: zobrazení podřízených položek ve sloupcích pomocí ovládacího prvku Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-114">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-115">Popisuje postup zobrazení informací o jednotlivých položek ve sloupcích.</span><span class="sxs-lookup"><span data-stu-id="a11e1-115">Describes how to display information about each list item in columns.</span></span>  
  
 [<span data-ttu-id="a11e1-116">Postupy: vyberte položku v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="a11e1-116">How to: Select an Item in the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-117">Popisuje, jak prostřednictvím kódu programu vyberte položku.</span><span class="sxs-lookup"><span data-stu-id="a11e1-117">Describes how to programmatically select an item.</span></span>  
  
 [<span data-ttu-id="a11e1-118">Postupy: seskupení položek v systému Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-118">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-119">Popisuje, jak vytvořit skupiny pro seřazený podle kategorií zobrazení a přiřazení položky ke každé skupině.</span><span class="sxs-lookup"><span data-stu-id="a11e1-119">Describes how to create groups for categorized display and how to assign items to each group.</span></span>  
  
 <span data-ttu-id="a11e1-120">Tato funkce je dostupná pouze pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a11e1-120">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a11e1-121">Postupy: povolení zobrazení Tile v systému Windows Forms ListView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a11e1-121">How to: Enable Tile View in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-122">Popisuje, jak zobrazit položky jako dlaždice, z nichž každý se skládá z velkých ikon a více řádků textu.</span><span class="sxs-lookup"><span data-stu-id="a11e1-122">Describes how to display items as tiles, each of which is comprised of a large icon and multiple lines of text.</span></span>  
  
 <span data-ttu-id="a11e1-123">Tato funkce je dostupná pouze pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a11e1-123">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a11e1-124">Postupy: zobrazení značky vložení v ovládacím prvku Windows Forms ListView</span><span class="sxs-lookup"><span data-stu-id="a11e1-124">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 <span data-ttu-id="a11e1-125">Popisuje, jak implementovat zpětnou vazbu od uživatelů pro operace přetahování myší, ve kterých značky vložení Určuje umístění drop pro každý ukazatel myši pozici.</span><span class="sxs-lookup"><span data-stu-id="a11e1-125">Describes how to implement user-feedback for drag-and-drop operations in which an insertion mark indicates the drop location for each mouse-pointer position.</span></span>  
  
 <span data-ttu-id="a11e1-126">Tato funkce je dostupná pouze pro [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a11e1-126">This feature is available only for [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)].</span></span>  
  
 [<span data-ttu-id="a11e1-127">Postupy: přidání schopností vyhledávání do ovládacího prvku ListView</span><span class="sxs-lookup"><span data-stu-id="a11e1-127">How to: Add Search Capabilities to a ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 <span data-ttu-id="a11e1-128">Popisuje, jak programově najít položku pomocí buď textové vyhledávání nebo obrazovky souřadnice.</span><span class="sxs-lookup"><span data-stu-id="a11e1-128">Describes how to programmatically find an item using either text search or screen coordinates.</span></span>  
  
-   <span data-ttu-id="a11e1-129">[Postupy: povolení zobrazení Tile v systému Windows Forms ListView pomocí návrháře](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a11e1-129">[How to: Enable Tile View in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233655\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a11e1-130">[Postupy: Přidání a odebrání položek pomocí ovládacího prvku Windows Forms ListView pomocí návrháře](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a11e1-130">[How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233671\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a11e1-131">[Postupy: Přidání sloupců do ovládacího prvku Windows Forms ListView pomocí návrháře](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a11e1-131">[How to: Add Columns to the Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233652\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a11e1-132">[Postupy: seskupení položek v systému Windows Forms ListView pomocí návrháře](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a11e1-132">[How to: Group Items in a Windows Forms ListView Control Using the Designer](http://msdn.microsoft.com/library/ms233663\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="a11e1-133">[Návod: Vytváření rozhraní ve stylu Průzkumníku s prvky ListView a TreeView pomocí návrháře](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="a11e1-133">[Walkthrough: Creating an Explorer Style Interface with the ListView and TreeView Controls Using the Designer](http://msdn.microsoft.com/library/ms171645\(v=vs.110\))</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a11e1-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="a11e1-134">Reference</span></span>  
 <span data-ttu-id="a11e1-135"><xref:System.Windows.Forms.ListView>– Třída</span><span class="sxs-lookup"><span data-stu-id="a11e1-135"><xref:System.Windows.Forms.ListView> class</span></span>  
 <span data-ttu-id="a11e1-136">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="a11e1-136">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a11e1-137">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a11e1-137">Related Sections</span></span>  
 [<span data-ttu-id="a11e1-138">Postupy: Přidání vlastních informací do prvku TreeView nebo ListView – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a11e1-138">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 <span data-ttu-id="a11e1-139">Popisuje, jak dědit z položku v zobrazení seznamu nebo uzel v zobrazení stromu, aby bylo možné přidat žádné pole, metody nebo konstruktory, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a11e1-139">Describes how to inherit from an item in a list view or a node in a tree view in order to add any fields, methods, or constructors you need.</span></span>  
  
 [<span data-ttu-id="a11e1-140">ImageList – komponenta</span><span class="sxs-lookup"><span data-stu-id="a11e1-140">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 <span data-ttu-id="a11e1-141">Vysvětluje, co seznamu obrázků a jeho klíčové funkce a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a11e1-141">Explains what an image list is and its key features and properties.</span></span>  
  
 [<span data-ttu-id="a11e1-142">Postupy: vytváření více podokny uživatelského rozhraní s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a11e1-142">How to: Create a Multipane User Interface with Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 <span data-ttu-id="a11e1-143">Poskytuje pokyny pro vytvoření rozložení formuláře Windows s více podokny.</span><span class="sxs-lookup"><span data-stu-id="a11e1-143">Gives instructions for laying out a Windows Form with multiple panes.</span></span>  
  
 [<span data-ttu-id="a11e1-144">Funkce systému Windows XP a Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="a11e1-144">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 <span data-ttu-id="a11e1-145">Vysvětluje, jak využívat funkce specifické pro systém Windows XP, která se týkají <xref:System.Windows.Forms.ListView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a11e1-145">Explains how to take advantage of Windows XP-specific features that apply to the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a11e1-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="a11e1-146">See Also</span></span>  
 [<span data-ttu-id="a11e1-147">Ovládací prvky používané ve formulářích Windows</span><span class="sxs-lookup"><span data-stu-id="a11e1-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
