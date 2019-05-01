---
title: Zobrazení dat v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: c153d422470ff20491567aed70557e461dc2b4e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972221"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ab79a-102">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ab79a-103">`DataGridView` Ovládacího prvku se používá k zobrazení dat z různých zdrojů externí data.</span><span class="sxs-lookup"><span data-stu-id="ab79a-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="ab79a-104">Alternativně můžete přidávání řádků a sloupců do ovládacího prvku a ručně ho naplnit daty.</span><span class="sxs-lookup"><span data-stu-id="ab79a-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="ab79a-105">Když vazbu ovládacího prvku do zdroje dat, můžete generovat automaticky na základě schématu zdroje dat sloupce.</span><span class="sxs-lookup"><span data-stu-id="ab79a-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="ab79a-106">Pokud tyto sloupce se nezobrazují stejně, jako je chcete, můžete skrýt, odebrat nebo změnit jejich pořadí.</span><span class="sxs-lookup"><span data-stu-id="ab79a-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="ab79a-107">Můžete také přidat nevázaných sloupců zobrazíte dodatečná data, která nepochází z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="ab79a-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="ab79a-108">Kromě toho můžete zobrazit svá data pomocí standardních formátech (například formát měny), nebo můžete přizpůsobit zobrazení formátování k prezentaci dat, ale budete muset (jako je například změna barvy pozadí pro záporná čísla nebo nahrazením hodnoty řetězce s odpovídající Image).</span><span class="sxs-lookup"><span data-stu-id="ab79a-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab79a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ab79a-109">In This Section</span></span>  
 [<span data-ttu-id="ab79a-110">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-111">Popisuje možnosti pro naplnění ovládacího prvku s daty.</span><span class="sxs-lookup"><span data-stu-id="ab79a-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="ab79a-112">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-113">Popisuje možnosti pro formátování hodnot v buňkách zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ab79a-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="ab79a-114">Návod: Vytvoření nevázaného Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="ab79a-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-115">Popisuje, jak ručně naplnění ovládacího prvku s daty.</span><span class="sxs-lookup"><span data-stu-id="ab79a-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="ab79a-116">Postupy: Vytvoření vazby dat na ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-117">Popisuje, jak naplnit pomocí vytvoření vazby na ovládací prvek s daty `BindingSource` , který obsahuje informace o získaných z databáze.</span><span class="sxs-lookup"><span data-stu-id="ab79a-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="ab79a-118">Postupy: Automatické generování sloupců v ovládacím prvku DataGridView vázaných na Data Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab79a-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="ab79a-119">Popisuje, jak automaticky vygenerovat sloupce na základě vázaných dat zdroje.</span><span class="sxs-lookup"><span data-stu-id="ab79a-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="ab79a-120">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="ab79a-121">Popisuje, jak skrýt nebo odstranění sloupců, které jsou generovány z připojených dat zdroje.</span><span class="sxs-lookup"><span data-stu-id="ab79a-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="ab79a-122">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-123">Popisuje, jak změnit uspořádání sloupců, které jsou generovány z připojených dat zdroje.</span><span class="sxs-lookup"><span data-stu-id="ab79a-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="ab79a-124">Postupy: Přidání nepřipojeného sloupce do ovládacího prvku DataGridView vázaný na Data Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab79a-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="ab79a-125">Popisuje postup doplňují data ze zdroje vázaných dat tím, že zobrazuje další, nevázaného sloupce.</span><span class="sxs-lookup"><span data-stu-id="ab79a-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="ab79a-126">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="ab79a-127">Popisuje, jak vytvořit vazbu ovládacího prvku kolekce objektů libovolného tak, aby každý objekt se zobrazí v samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="ab79a-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="ab79a-128">Postupy: Přístup k objektům Svázaným Windows Forms DataGridView řádků</span><span class="sxs-lookup"><span data-stu-id="ab79a-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="ab79a-129">Popisuje, jak získat objekt vázán na konkrétní řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ab79a-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="ab79a-130">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="ab79a-131">Popisuje, jak zobrazit data ze dvou tabulek souvisejících databáze tak, aby hodnoty zobrazené v jednom `DataGridView` ovládací prvek závisí na aktuálně vybraný řádek v jiném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ab79a-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="ab79a-132">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-133">Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> události a změně vzhledu buněk v závislosti na jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ab79a-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ab79a-134">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ab79a-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="ab79a-135">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ab79a-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="ab79a-136">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ab79a-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="ab79a-137">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ab79a-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab79a-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ab79a-138">Related Sections</span></span>  
 [<span data-ttu-id="ab79a-139">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ab79a-140">Obsahuje témata, která popisují, jak změnit způsob, jak uživatelé přidávat a upravovat data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ab79a-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab79a-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab79a-141">See also</span></span>

- [<span data-ttu-id="ab79a-142">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="ab79a-143">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ab79a-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
