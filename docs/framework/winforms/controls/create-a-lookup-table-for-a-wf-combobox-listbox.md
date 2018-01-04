---
title: "Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f49a8fbd2cc8ffae94e4dcbbc4babf7c1137cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="ce347-102">Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="ce347-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="ce347-103">Někdy je užitečné zobrazit data ve formátu uživatelsky přívětivý ve formuláři Windows, ale ukládání dat do formátu, který je smysluplnější do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce347-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="ce347-104">Například může zobrazit formulář objednávky pro jídlo položek nabídky v seznamu s názvem.</span><span class="sxs-lookup"><span data-stu-id="ce347-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="ce347-105">Datová tabulka záznam pořadí by však obsahovat jedinečná čísla ID představující jídlo.</span><span class="sxs-lookup"><span data-stu-id="ce347-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="ce347-106">Příklad toho, jak ukládat a zobrazit formulář objednávky data pro jídlo v následujících tabulkách.</span><span class="sxs-lookup"><span data-stu-id="ce347-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="ce347-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="ce347-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="ce347-108">OrderID</span><span class="sxs-lookup"><span data-stu-id="ce347-108">OrderID</span></span>|<span data-ttu-id="ce347-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="ce347-109">ItemID</span></span>|<span data-ttu-id="ce347-110">Množství</span><span class="sxs-lookup"><span data-stu-id="ce347-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="ce347-111">4085</span><span class="sxs-lookup"><span data-stu-id="ce347-111">4085</span></span>|<span data-ttu-id="ce347-112">12</span><span class="sxs-lookup"><span data-stu-id="ce347-112">12</span></span>|<span data-ttu-id="ce347-113">1</span><span class="sxs-lookup"><span data-stu-id="ce347-113">1</span></span>|  
|<span data-ttu-id="ce347-114">4086</span><span class="sxs-lookup"><span data-stu-id="ce347-114">4086</span></span>|<span data-ttu-id="ce347-115">13</span><span class="sxs-lookup"><span data-stu-id="ce347-115">13</span></span>|<span data-ttu-id="ce347-116">3</span><span class="sxs-lookup"><span data-stu-id="ce347-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="ce347-117">ItemTable</span><span class="sxs-lookup"><span data-stu-id="ce347-117">ItemTable</span></span>  
  
|<span data-ttu-id="ce347-118">ID</span><span class="sxs-lookup"><span data-stu-id="ce347-118">ID</span></span>|<span data-ttu-id="ce347-119">Název</span><span class="sxs-lookup"><span data-stu-id="ce347-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="ce347-120">12</span><span class="sxs-lookup"><span data-stu-id="ce347-120">12</span></span>|<span data-ttu-id="ce347-121">Určené</span><span class="sxs-lookup"><span data-stu-id="ce347-121">Potato</span></span>|  
|<span data-ttu-id="ce347-122">13</span><span class="sxs-lookup"><span data-stu-id="ce347-122">13</span></span>|<span data-ttu-id="ce347-123">Kuřecí</span><span class="sxs-lookup"><span data-stu-id="ce347-123">Chicken</span></span>|  
  
 <span data-ttu-id="ce347-124">V tomto scénáři, jedna tabulka, **OrderDetailsTable**, ukládá informace jste se zobrazení a ukládání.</span><span class="sxs-lookup"><span data-stu-id="ce347-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="ce347-125">Ušetřit místo, se ale tak poměrně jako nesrozumitelné způsobem.</span><span class="sxs-lookup"><span data-stu-id="ce347-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="ce347-126">V tabulce **ItemTable**, obsahuje pouze informace týkající se vzhled o které ID číslo je ekvivalentní, na které jídlo název a nic o skutečné jídlo objednávky.</span><span class="sxs-lookup"><span data-stu-id="ce347-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="ce347-127">**ItemTable** je připojený k <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> řízení prostřednictvím tři vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce347-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="ce347-128">`DataSource` Vlastnost obsahuje název této tabulky.</span><span class="sxs-lookup"><span data-stu-id="ce347-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="ce347-129">`DisplayMember` Vlastnost obsahuje sloupce dat z této tabulky, které chcete zobrazit v ovládacím prvku (název jídlo).</span><span class="sxs-lookup"><span data-stu-id="ce347-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="ce347-130">`ValueMember` Vlastnost obsahuje sloupce dat této tabulky s uložené informace (číslo ID).</span><span class="sxs-lookup"><span data-stu-id="ce347-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="ce347-131">**OrderDetailsTable** je připojen k ovládacímu prvku jeho vazby kolekce přistupovat prostřednictvím <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ce347-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="ce347-132">Když přidáte objekt vazby ke kolekci, připojíte vlastnost ovládacího prvku na konkrétní data člena (sloupec ID čísla) ve zdroji dat ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="ce347-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="ce347-133">Při výběru v ovládacím prvku, je tato tabulka uložení vstup formuláře.</span><span class="sxs-lookup"><span data-stu-id="ce347-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="ce347-134">K vytvoření vyhledávací tabulky</span><span class="sxs-lookup"><span data-stu-id="ce347-134">To create a lookup table</span></span>  
  
1.  <span data-ttu-id="ce347-135">Přidat <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, nebo <xref:System.Windows.Forms.CheckedListBox> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ce347-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2.  <span data-ttu-id="ce347-136">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ce347-136">Connect to your data source.</span></span>  
  
3.  <span data-ttu-id="ce347-137">Vytvořte vztah data mezi dvěma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="ce347-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="ce347-138">V tématu [Úvod do objektů DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span><span class="sxs-lookup"><span data-stu-id="ce347-138">See [Introduction to DataRelation Objects](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).</span></span>  
  
4.  <span data-ttu-id="ce347-139">Nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce347-139">Set the following properties.</span></span> <span data-ttu-id="ce347-140">Lze nastavit v kódu nebo v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ce347-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="ce347-141">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ce347-141">Property</span></span>|<span data-ttu-id="ce347-142">Nastavení</span><span class="sxs-lookup"><span data-stu-id="ce347-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="ce347-143">Tabulka, která obsahuje informace o ID, které se rovná která položka číslo.</span><span class="sxs-lookup"><span data-stu-id="ce347-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="ce347-144">V předchozím scénáři je to `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="ce347-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="ce347-145">Sloupec tabulky zdroje dat, která chcete zobrazit v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="ce347-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="ce347-146">V předchozím scénáři je to `"Name"` (Pokud chcete nastavit v kódu, použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="ce347-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="ce347-147">Sloupec tabulky zdroje dat, která obsahuje informace o uložené.</span><span class="sxs-lookup"><span data-stu-id="ce347-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="ce347-148">V předchozím scénáři je to `"ID"` (Pokud chcete nastavit v kódu, použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="ce347-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5.  <span data-ttu-id="ce347-149">V postupu, volání <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metodu <xref:System.Windows.Forms.ControlBindingsCollection> třídy pro vazbu ovládacího prvku <xref:System.Windows.Forms.ListControl.SelectedValue%2A> vlastnost, která má v tabulce zaznamenávání vstup formuláře.</span><span class="sxs-lookup"><span data-stu-id="ce347-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="ce347-150">Můžete také to provedete v Návrháři místo v kódu, přístup k ovládacího prvku <xref:System.Windows.Forms.Control.DataBindings%2A> vlastnost **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="ce347-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="ce347-151">V předchozím scénáři je to `OrderDetailsTable`, a sloupec je `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="ce347-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ce347-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce347-152">See Also</span></span>  
 [<span data-ttu-id="ce347-153">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce347-153">Data Binding and Windows Forms</span></span>](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="ce347-154">Přehled ovládacího prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="ce347-154">ListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="ce347-155">Přehled ovládacího prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="ce347-155">ComboBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [<span data-ttu-id="ce347-156">Přehled ovládacího prvku CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="ce347-156">CheckedListBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="ce347-157">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="ce347-157">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
