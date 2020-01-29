---
title: Vytvoření vyhledávací tabulky pro ovládací prvek ComboBox, ListBox nebo CheckedListBox
ms.date: 03/30/2017
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
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737366"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="82405-102">Postupy: Vytvoření vyhledávací tabulky pro ovládací prvek Windows Forms ComboBox, ListBox nebo CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="82405-102">How to: Create a Lookup Table for a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="82405-103">Někdy je užitečné zobrazit data v uživatelsky přívětivém formátu formuláře Windows, ale data ukládat ve formátu, který je pro váš program smysluplnější.</span><span class="sxs-lookup"><span data-stu-id="82405-103">Sometimes it is useful to display data in a user-friendly format on a Windows Form, but store the data in a format that is more meaningful to your program.</span></span> <span data-ttu-id="82405-104">Například formulář objednávky pro potraviny může zobrazit položky nabídky podle názvu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="82405-104">For example, an order form for food might display the menu items by name in a list box.</span></span> <span data-ttu-id="82405-105">Data, která záznam obsahuje, ale budou obsahovat jedinečná čísla ID představující jídlo.</span><span class="sxs-lookup"><span data-stu-id="82405-105">However, the data table recording the order would contain the unique ID numbers representing the food.</span></span> <span data-ttu-id="82405-106">V následujících tabulkách je uveden příklad ukládání a zobrazení dat z pořadí pro potraviny.</span><span class="sxs-lookup"><span data-stu-id="82405-106">The following tables show an example of how to store and display order-form data for food.</span></span>  
  
### <a name="orderdetailstable"></a><span data-ttu-id="82405-107">OrderDetailsTable</span><span class="sxs-lookup"><span data-stu-id="82405-107">OrderDetailsTable</span></span>  
  
|<span data-ttu-id="82405-108">Seskup</span><span class="sxs-lookup"><span data-stu-id="82405-108">OrderID</span></span>|<span data-ttu-id="82405-109">ItemID</span><span class="sxs-lookup"><span data-stu-id="82405-109">ItemID</span></span>|<span data-ttu-id="82405-110">Množství</span><span class="sxs-lookup"><span data-stu-id="82405-110">Quantity</span></span>|  
|-------------|------------|--------------|  
|<span data-ttu-id="82405-111">4085</span><span class="sxs-lookup"><span data-stu-id="82405-111">4085</span></span>|<span data-ttu-id="82405-112">12</span><span class="sxs-lookup"><span data-stu-id="82405-112">12</span></span>|<span data-ttu-id="82405-113">1</span><span class="sxs-lookup"><span data-stu-id="82405-113">1</span></span>|  
|<span data-ttu-id="82405-114">4086</span><span class="sxs-lookup"><span data-stu-id="82405-114">4086</span></span>|<span data-ttu-id="82405-115">13</span><span class="sxs-lookup"><span data-stu-id="82405-115">13</span></span>|<span data-ttu-id="82405-116">3</span><span class="sxs-lookup"><span data-stu-id="82405-116">3</span></span>|  
  
### <a name="itemtable"></a><span data-ttu-id="82405-117">Položkace</span><span class="sxs-lookup"><span data-stu-id="82405-117">ItemTable</span></span>  
  
|<span data-ttu-id="82405-118">ID</span><span class="sxs-lookup"><span data-stu-id="82405-118">ID</span></span>|<span data-ttu-id="82405-119">Name</span><span class="sxs-lookup"><span data-stu-id="82405-119">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="82405-120">12</span><span class="sxs-lookup"><span data-stu-id="82405-120">12</span></span>|<span data-ttu-id="82405-121">Hlíz</span><span class="sxs-lookup"><span data-stu-id="82405-121">Potato</span></span>|  
|<span data-ttu-id="82405-122">13</span><span class="sxs-lookup"><span data-stu-id="82405-122">13</span></span>|<span data-ttu-id="82405-123">Nainstalováním</span><span class="sxs-lookup"><span data-stu-id="82405-123">Chicken</span></span>|  
  
 <span data-ttu-id="82405-124">V tomto scénáři jedna tabulka **OrderDetailsTable**ukládá skutečné informace, které se týkají zobrazení a uložení.</span><span class="sxs-lookup"><span data-stu-id="82405-124">In this scenario, one table, **OrderDetailsTable**, stores the actual information you are concerned with displaying and saving.</span></span> <span data-ttu-id="82405-125">Pokud ale chcete ušetřit místo, je to poměrně nešifrovaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="82405-125">But to save space, it does so in a fairly cryptic fashion.</span></span> <span data-ttu-id="82405-126">Druhá tabulka, **položka**, obsahuje pouze informace o vzhledu, jejichž číslo ID je ekvivalentní k tomu, který název potravy a nic o skutečných seřazeních potravin.</span><span class="sxs-lookup"><span data-stu-id="82405-126">The other table, **ItemTable**, contains only appearance-related information about which ID number is equivalent to which food name, and nothing about the actual food orders.</span></span>  
  
 <span data-ttu-id="82405-127">Vlastnost **Item** je připojena k ovládacímu prvku <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>nebo <xref:System.Windows.Forms.CheckedListBox> prostřednictvím tří vlastností.</span><span class="sxs-lookup"><span data-stu-id="82405-127">The **ItemTable** is connected to the <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control through three properties.</span></span> <span data-ttu-id="82405-128">Vlastnost `DataSource` obsahuje název této tabulky.</span><span class="sxs-lookup"><span data-stu-id="82405-128">The `DataSource` property contains the name of this table.</span></span> <span data-ttu-id="82405-129">Vlastnost `DisplayMember` obsahuje datový sloupec této tabulky, který chcete zobrazit v ovládacím prvku (název potravy).</span><span class="sxs-lookup"><span data-stu-id="82405-129">The `DisplayMember` property contains the data column of that table that you want to display in the control (the food name).</span></span> <span data-ttu-id="82405-130">Vlastnost `ValueMember` obsahuje datový sloupec v tabulce s uloženými informacemi (číslo ID).</span><span class="sxs-lookup"><span data-stu-id="82405-130">The `ValueMember` property contains the data column of that table with the stored information (the ID number).</span></span>  
  
 <span data-ttu-id="82405-131">**OrderDetailsTable** je připojen k ovládacímu prvku prostřednictvím kolekce vazeb, ke kterému se přistupoval prostřednictvím vlastnosti <xref:System.Windows.Forms.Control.DataBindings%2A>.</span><span class="sxs-lookup"><span data-stu-id="82405-131">The **OrderDetailsTable** is connected to the control by its bindings collection, accessed through the <xref:System.Windows.Forms.Control.DataBindings%2A> property.</span></span> <span data-ttu-id="82405-132">Když přidáte objekt vazby do kolekce, připojíte vlastnost ovládacího prvku ke konkrétnímu datovému členu (sloupci čísel ID) ve zdroji dat ( **OrderDetailsTable**).</span><span class="sxs-lookup"><span data-stu-id="82405-132">When you add a binding object to the collection, you connect a control property to a specific data member (the column of ID numbers) in a data source (the **OrderDetailsTable**).</span></span> <span data-ttu-id="82405-133">V případě, že je v ovládacím prvku proveden výběr, v této tabulce je uložen vstup z formuláře.</span><span class="sxs-lookup"><span data-stu-id="82405-133">When a selection is made in the control, this table is where the form input is saved.</span></span>  
  
### <a name="to-create-a-lookup-table"></a><span data-ttu-id="82405-134">Vytvoření vyhledávací tabulky</span><span class="sxs-lookup"><span data-stu-id="82405-134">To create a lookup table</span></span>  
  
1. <span data-ttu-id="82405-135">Do formuláře přidejte ovládací prvek <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>nebo <xref:System.Windows.Forms.CheckedListBox>.</span><span class="sxs-lookup"><span data-stu-id="82405-135">Add a <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, or <xref:System.Windows.Forms.CheckedListBox> control to the form.</span></span>  
  
2. <span data-ttu-id="82405-136">Připojte se ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="82405-136">Connect to your data source.</span></span>  
  
3. <span data-ttu-id="82405-137">Vytvořte datový vztah mezi oběma tabulkami.</span><span class="sxs-lookup"><span data-stu-id="82405-137">Establish a data relation between the two tables.</span></span> <span data-ttu-id="82405-138">Viz [Úvod do objektů DataRelation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="82405-138">See [Introduction to DataRelation Objects](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120)).</span></span>  
  
4. <span data-ttu-id="82405-139">Nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="82405-139">Set the following properties.</span></span> <span data-ttu-id="82405-140">Můžou být nastavené v kódu nebo v návrháři.</span><span class="sxs-lookup"><span data-stu-id="82405-140">They can be set in code or in the designer.</span></span>  
  
    |<span data-ttu-id="82405-141">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="82405-141">Property</span></span>|<span data-ttu-id="82405-142">Nastavení</span><span class="sxs-lookup"><span data-stu-id="82405-142">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|<span data-ttu-id="82405-143">Tabulka obsahující informace o tom, které číslo ID je ekvivalentní k této položce.</span><span class="sxs-lookup"><span data-stu-id="82405-143">The table that contains information about which ID number is equivalent to which item.</span></span> <span data-ttu-id="82405-144">V předchozím scénáři je to `ItemTable`.</span><span class="sxs-lookup"><span data-stu-id="82405-144">In the previous scenario, this is `ItemTable`.</span></span>|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|<span data-ttu-id="82405-145">Sloupec tabulky zdroje dat, který chcete zobrazit v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="82405-145">The column of the data source table that you want to display in the control.</span></span> <span data-ttu-id="82405-146">V předchozím scénáři se jedná o `"Name"` (pro nastavení v kódu použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="82405-146">In the previous scenario, this is `"Name"` (to set in code, use quotation marks).</span></span>|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|<span data-ttu-id="82405-147">Sloupec tabulky zdroje dat, který obsahuje uložené informace.</span><span class="sxs-lookup"><span data-stu-id="82405-147">The column of the data source table that contains the stored information.</span></span> <span data-ttu-id="82405-148">V předchozím scénáři se jedná o `"ID"` (pro nastavení v kódu použijte uvozovky).</span><span class="sxs-lookup"><span data-stu-id="82405-148">In the previous scenario, this is `"ID"` (to set in code, use quotation marks).</span></span>|  
  
5. <span data-ttu-id="82405-149">V proceduře zavolejte metodu <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> třídy <xref:System.Windows.Forms.ControlBindingsCollection>, abyste navázali vlastnost <xref:System.Windows.Forms.ListControl.SelectedValue%2A> ovládacího prvku na tabulku zaznamenávající vstup formuláře.</span><span class="sxs-lookup"><span data-stu-id="82405-149">In a procedure, call the <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> method of the <xref:System.Windows.Forms.ControlBindingsCollection> class to bind the control's <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property to the table recording the form input.</span></span> <span data-ttu-id="82405-150">Můžete to provést také v Návrháři místo v kódu, a to tak, že v okně **vlastnosti** přistupujete k vlastnosti <xref:System.Windows.Forms.Control.DataBindings%2A> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82405-150">You can also do this in the Designer instead of in code, by accessing the control's <xref:System.Windows.Forms.Control.DataBindings%2A> property in the **Properties** window.</span></span> <span data-ttu-id="82405-151">V předchozím scénáři je to `OrderDetailsTable`a sloupec je `"ItemID"`.</span><span class="sxs-lookup"><span data-stu-id="82405-151">In the previous scenario, this is `OrderDetailsTable`, and the column is `"ItemID"`.</span></span>  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="82405-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82405-152">See also</span></span>

- [<span data-ttu-id="82405-153">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82405-153">Data Binding and Windows Forms</span></span>](../data-binding-and-windows-forms.md)
- [<span data-ttu-id="82405-154">Přehled ovládacího prvku ListBox</span><span class="sxs-lookup"><span data-stu-id="82405-154">ListBox Control Overview</span></span>](listbox-control-overview-windows-forms.md)
- [<span data-ttu-id="82405-155">Přehled ovládacího prvku ComboBox</span><span class="sxs-lookup"><span data-stu-id="82405-155">ComboBox Control Overview</span></span>](combobox-control-overview-windows-forms.md)
- [<span data-ttu-id="82405-156">Přehled ovládacího prvku CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="82405-156">CheckedListBox Control Overview</span></span>](checkedlistbox-control-overview-windows-forms.md)
- [<span data-ttu-id="82405-157">Ovládací prvky Windows Forms používané k výpisu možností</span><span class="sxs-lookup"><span data-stu-id="82405-157">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
