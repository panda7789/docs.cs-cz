---
title: Zobrazení dat v ovládacím prvku DataGridView
description: Naučte se používat ovládací prvek DataGridView model Windows Forms k zobrazení dat z nejrůznějších externích zdrojů dat.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174572"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0ae33-103">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0ae33-104">`DataGridView`Ovládací prvek slouží k zobrazení dat z nejrůznějších externích zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="0ae33-105">Alternativně můžete k ovládacímu prvku přidat řádky a sloupce a ručně ho vyplnit daty.</span><span class="sxs-lookup"><span data-stu-id="0ae33-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="0ae33-106">Když svážete ovládací prvek se zdrojem dat, můžete automaticky generovat sloupce založené na schématu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="0ae33-107">Pokud se tyto sloupce nezobrazí tak, jak chcete, můžete je skrýt, odebrat nebo změnit jejich uspořádání.</span><span class="sxs-lookup"><span data-stu-id="0ae33-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="0ae33-108">Přidáním nevázaných sloupců taky můžete zobrazit doplňková data, která nepochází ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="0ae33-109">Navíc můžete zobrazit vaše data pomocí standardních formátů (například formátu měny) nebo můžete přizpůsobit formátování zobrazení, abyste mohli prezentovat data, ale potřebujete (například změnit barvu pozadí pro záporná čísla nebo nahradit hodnoty řetězce odpovídajícími obrázky).</span><span class="sxs-lookup"><span data-stu-id="0ae33-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ae33-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0ae33-110">In This Section</span></span>  
 [<span data-ttu-id="0ae33-111">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-112">Popisuje možnosti pro naplnění ovládacího prvku daty.</span><span class="sxs-lookup"><span data-stu-id="0ae33-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="0ae33-113">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-114">Popisuje možnosti formátování hodnot zobrazení buňky.</span><span class="sxs-lookup"><span data-stu-id="0ae33-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="0ae33-115">Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-116">V této části najdete popis postupu ručního naplnění ovládacího prvku daty.</span><span class="sxs-lookup"><span data-stu-id="0ae33-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="0ae33-117">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-118">Popisuje, jak naplnit ovládací prvek daty tak, že je sváže s objektem `BindingSource` , který obsahuje informace načtené z databáze.</span><span class="sxs-lookup"><span data-stu-id="0ae33-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="0ae33-119">Postupy: Automatické generování sloupců v daty připojeném ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="0ae33-120">Popisuje, jak automaticky generovat sloupce založené na vázaném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="0ae33-121">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="0ae33-122">Popisuje, jak skrýt nebo odstranit sloupce vygenerované automaticky z vázaného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="0ae33-123">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-124">Popisuje, jak změnit uspořádání sloupců vygenerovaných automaticky z vázaného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0ae33-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="0ae33-125">Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="0ae33-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="0ae33-126">Popisuje, jak doplnit data z vázaného zdroje dat zobrazením dalších nevázaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="0ae33-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="0ae33-127">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="0ae33-128">Popisuje, jak navazovat ovládací prvek na kolekci libovolných objektů, aby se každý objekt zobrazoval na vlastním řádku.</span><span class="sxs-lookup"><span data-stu-id="0ae33-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="0ae33-129">Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="0ae33-130">Popisuje, jak načíst objekt vázaný na konkrétní řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0ae33-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="0ae33-131">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="0ae33-132">Popisuje, jak zobrazit data ze dvou souvisejících databázových tabulek, aby hodnoty zobrazené v jednom `DataGridView` ovládacím prvku byly závislé na aktuálně vybraném řádku v jiném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0ae33-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="0ae33-133">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-134">Popisuje, jak zpracovat <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událost ke změně vzhledu buněk v závislosti na jejich hodnotách.</span><span class="sxs-lookup"><span data-stu-id="0ae33-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0ae33-135">Reference</span><span class="sxs-lookup"><span data-stu-id="0ae33-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="0ae33-136">Poskytuje referenční dokumentaci k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="0ae33-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="0ae33-137">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0ae33-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="0ae33-138">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponentu.</span><span class="sxs-lookup"><span data-stu-id="0ae33-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0ae33-139">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0ae33-139">Related Sections</span></span>  
 [<span data-ttu-id="0ae33-140">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0ae33-141">Poskytuje témata, která popisují, jak změnit způsob, jakým uživatelé přidávají a upravují data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0ae33-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae33-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ae33-142">See also</span></span>

- [<span data-ttu-id="0ae33-143">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="0ae33-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="0ae33-144">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0ae33-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
