---
title: Zobrazení dat v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d02362895d75df3735d19554bd44bb8ac443c6c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745877"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="0f136-102">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="0f136-103">`DataGridView` ovládací prvek slouží k zobrazení dat z nejrůznějších externích zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="0f136-104">Alternativně můžete k ovládacímu prvku přidat řádky a sloupce a ručně ho vyplnit daty.</span><span class="sxs-lookup"><span data-stu-id="0f136-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="0f136-105">Když svážete ovládací prvek se zdrojem dat, můžete automaticky generovat sloupce založené na schématu zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="0f136-106">Pokud se tyto sloupce nezobrazí tak, jak chcete, můžete je skrýt, odebrat nebo změnit jejich uspořádání.</span><span class="sxs-lookup"><span data-stu-id="0f136-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="0f136-107">Přidáním nevázaných sloupců taky můžete zobrazit doplňková data, která nepochází ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="0f136-108">Navíc můžete zobrazit vaše data pomocí standardních formátů (například formátu měny) nebo můžete přizpůsobit formátování zobrazení, abyste mohli prezentovat data, ale potřebujete (například změnit barvu pozadí pro záporná čísla nebo nahrazovat hodnoty řetězců. s odpovídajícími bitovými kopiemi).</span><span class="sxs-lookup"><span data-stu-id="0f136-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f136-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0f136-109">In This Section</span></span>  
 [<span data-ttu-id="0f136-110">Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-111">Popisuje možnosti pro naplnění ovládacího prvku daty.</span><span class="sxs-lookup"><span data-stu-id="0f136-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="0f136-112">Formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-113">Popisuje možnosti formátování hodnot zobrazení buňky.</span><span class="sxs-lookup"><span data-stu-id="0f136-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="0f136-114">Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-115">V této části najdete popis postupu ručního naplnění ovládacího prvku daty.</span><span class="sxs-lookup"><span data-stu-id="0f136-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="0f136-116">Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-117">Popisuje, jak naplnit ovládací prvek daty tak, že je sváže s `BindingSource`, která obsahuje informace načtené z databáze.</span><span class="sxs-lookup"><span data-stu-id="0f136-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="0f136-118">Postupy: Automatické generování sloupců v ovládacím prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="0f136-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="0f136-119">Popisuje, jak automaticky generovat sloupce založené na vázaném zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="0f136-120">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="0f136-121">Popisuje, jak skrýt nebo odstranit sloupce vygenerované automaticky z vázaného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="0f136-122">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-123">Popisuje, jak změnit uspořádání sloupců vygenerovaných automaticky z vázaného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0f136-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="0f136-124">Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou</span><span class="sxs-lookup"><span data-stu-id="0f136-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="0f136-125">Popisuje, jak doplnit data z vázaného zdroje dat zobrazením dalších nevázaných sloupců.</span><span class="sxs-lookup"><span data-stu-id="0f136-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="0f136-126">Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="0f136-127">Popisuje, jak navazovat ovládací prvek na kolekci libovolných objektů, aby se každý objekt zobrazoval na vlastním řádku.</span><span class="sxs-lookup"><span data-stu-id="0f136-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="0f136-128">Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="0f136-129">Popisuje, jak načíst objekt vázaný na konkrétní řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0f136-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="0f136-130">Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="0f136-131">Popisuje, jak zobrazit data ze dvou souvisejících databázových tabulek, aby hodnoty zobrazené v jednom ovládacím prvku `DataGridView` záviset na aktuálně vybraném řádku v jiném ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0f136-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="0f136-132">Postupy: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-133">Popisuje, jak zpracovat událost <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> pro změnu vzhledu buněk v závislosti na jejich hodnotách.</span><span class="sxs-lookup"><span data-stu-id="0f136-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f136-134">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="0f136-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="0f136-135">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="0f136-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="0f136-136">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f136-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="0f136-137">Poskytuje referenční dokumentaci pro součást <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0f136-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0f136-138">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0f136-138">Related Sections</span></span>  
 [<span data-ttu-id="0f136-139">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="0f136-140">Poskytuje témata, která popisují, jak změnit způsob, jakým uživatelé přidávají a upravují data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="0f136-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f136-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f136-141">See also</span></span>

- [<span data-ttu-id="0f136-142">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="0f136-143">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="0f136-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
