---
title: "Zobrazení dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 193562b5dd00950ec483da94e2ea6ea059e88805
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c967f-102">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c967f-103">`DataGridView` Řízení se používá k zobrazení dat z různých zdrojů externí data.</span><span class="sxs-lookup"><span data-stu-id="c967f-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="c967f-104">Alternativně můžete přidávání řádků a sloupců do ovládacího prvku a ručně přidejte do ní data.</span><span class="sxs-lookup"><span data-stu-id="c967f-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="c967f-105">Při vytvoření vazby ovládacího prvku ke zdroji dat, můžete vygenerovat automaticky na základě schématu zdroje dat sloupců.</span><span class="sxs-lookup"><span data-stu-id="c967f-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="c967f-106">Pokud tyto sloupce nezobrazí stejně, jako je chcete, můžete skrýt, odebrat nebo změna uspořádání je.</span><span class="sxs-lookup"><span data-stu-id="c967f-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="c967f-107">Můžete také přidat nevázaných sloupců zobrazíte dodatečná data, která nepochází z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="c967f-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="c967f-108">Kromě toho můžete zobrazit svá data pomocí standardní formáty (například formátu měny), nebo můžete přizpůsobit zobrazení formátování k prezentaci dat, ale budete muset (jako je například změna barvy pozadí pro záporná čísla nebo výměna řetězcové hodnoty pomocí odpovídající bitových kopií).</span><span class="sxs-lookup"><span data-stu-id="c967f-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c967f-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c967f-109">In This Section</span></span>  
 [<span data-ttu-id="c967f-110">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-111">Popisuje možnosti pro sestavování ovládacího prvku s daty.</span><span class="sxs-lookup"><span data-stu-id="c967f-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="c967f-112">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-113">Popisuje možnosti formátování hodnot v buňkách zobrazení.</span><span class="sxs-lookup"><span data-stu-id="c967f-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="c967f-114">Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-115">Popisuje, jak ručně naplnit ovládací prvek s daty.</span><span class="sxs-lookup"><span data-stu-id="c967f-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="c967f-116">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-117">Popisuje, jak k naplnění ovládacího prvku s daty pomocí vytvoření vazby, aby `BindingSource` obsahující informací načtených z databáze.</span><span class="sxs-lookup"><span data-stu-id="c967f-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="c967f-118">Postupy: Automatické generování sloupců v ovládacím prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="c967f-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="c967f-119">Popisuje, jak lze automaticky generovat sloupce podle vázaný datový zdroj.</span><span class="sxs-lookup"><span data-stu-id="c967f-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="c967f-120">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="c967f-121">Popisuje, jak můžete skrýt nebo odstranit sloupce, které automaticky generují z vázaný datový zdroj.</span><span class="sxs-lookup"><span data-stu-id="c967f-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="c967f-122">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-123">Popisuje, jak ke změně uspořádání sloupců generovaných automaticky z vázaný datový zdroj.</span><span class="sxs-lookup"><span data-stu-id="c967f-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="c967f-124">Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="c967f-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="c967f-125">Popisuje postup doplňují data z vázaný datový zdroj zobrazením Další, nevázaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="c967f-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="c967f-126">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="c967f-127">Popisuje, jak vytvořit vazbu ovládacího prvku do skupiny libovolný objekty tak, aby každý objekt je zobrazen na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="c967f-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="c967f-128">Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="c967f-129">Popisuje, jak načíst objekt vázaný na konkrétní řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c967f-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="c967f-130">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="c967f-131">Popisuje, jak zobrazit data ze dvou tabulek souvisejících databáze tak, aby hodnoty zobrazené v jednom `DataGridView` řízení závisí na aktuálně vybraný řádek v jiném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c967f-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="c967f-132">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-133">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí Změna vzhledu buněk v závislosti na jejich hodnot.</span><span class="sxs-lookup"><span data-stu-id="c967f-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c967f-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c967f-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c967f-135">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c967f-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c967f-136">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c967f-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="c967f-137">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="c967f-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c967f-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c967f-138">Related Sections</span></span>  
 [<span data-ttu-id="c967f-139">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-139">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c967f-140">Obsahuje témata, která popisují, jak změnit způsob uživatele, přidání a změna dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c967f-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c967f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="c967f-141">See Also</span></span>  
 [<span data-ttu-id="c967f-142">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="c967f-143">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c967f-143">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
