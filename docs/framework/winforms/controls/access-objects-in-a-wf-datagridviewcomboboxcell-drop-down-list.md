---
title: 'Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 221774895fa5867ad6ec870f7e293c9366e442f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080784"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="496f8-102">Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell</span><span class="sxs-lookup"><span data-stu-id="496f8-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="496f8-103">Podobně jako <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umožňují přidat libovolné objekty do rozevíracích seznamů.</span><span class="sxs-lookup"><span data-stu-id="496f8-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="496f8-104">Pomocí této funkce může představovat komplexní státy v rozevíracím seznamu bez nutnosti mít uložené odpovídající objekty v samostatné kolekce.</span><span class="sxs-lookup"><span data-stu-id="496f8-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="496f8-105">Na rozdíl od <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridView> typy nemají <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> vlastnost pro načtení aktuálně vybraného objektu.</span><span class="sxs-lookup"><span data-stu-id="496f8-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="496f8-106">Místo toho je nutné nastavit <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> nastavte na název vlastnosti pro objekt vaší firmy.</span><span class="sxs-lookup"><span data-stu-id="496f8-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="496f8-107">Když uživatel provede výběr, uvedené vlastnosti objektu obchodní nastaví buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="496f8-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="496f8-108">K načtení objektu firmy prostřednictvím její hodnotu `ValueMember` vlastnost musíte uvést vlastnost, která vrátí odkaz na samotný objekt firmy.</span><span class="sxs-lookup"><span data-stu-id="496f8-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="496f8-109">Proto pokud typ objektu obchodní není pod vaší kontrolou, je třeba přidat tato vlastnost rozšiřování typu prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="496f8-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="496f8-110">Následující postupy ukazují, jak naplnit rozevírací seznam pro obchodní objekty a načtení objektů prostřednictvím buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="496f8-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="496f8-111">Chcete-li přidat objekty obchodní rozevíracího seznamu</span><span class="sxs-lookup"><span data-stu-id="496f8-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="496f8-112">Vytvořte nový <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplnění jeho <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="496f8-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="496f8-113">Alternativně můžete nastavit sloupci <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> vlastností do kolekce pro obchodní objekty.</span><span class="sxs-lookup"><span data-stu-id="496f8-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="496f8-114">V takovém případě ale nemůže přidat "nepřiřazené" do rozevíracího seznamu bez vytvoření odpovídající obchodní objekt v kolekci.</span><span class="sxs-lookup"><span data-stu-id="496f8-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="496f8-115">Nastavte <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="496f8-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> <span data-ttu-id="496f8-116">Určuje vlastnost, která obchodního objektu, chcete-li zobrazit v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="496f8-116">indicates the property of the business object to display in the drop-down list.</span></span> <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> <span data-ttu-id="496f8-117">Určuje vlastnost, která vrátí odkaz na objekt firmy.</span><span class="sxs-lookup"><span data-stu-id="496f8-117">indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="496f8-118">Ujistěte se, že vaše obchodní typ objektu obsahuje vlastnost, která vrátí odkaz na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="496f8-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="496f8-119">Tato vlastnost musí mít název s hodnotou přiřazenou k <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="496f8-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="496f8-120">Aby se načetl objekt aktuálně vybrané obchodní</span><span class="sxs-lookup"><span data-stu-id="496f8-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="496f8-121">Získat buňku <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost a přetypujte ji pro obchodní typ objektu.</span><span class="sxs-lookup"><span data-stu-id="496f8-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="496f8-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="496f8-122">Example</span></span>  
 <span data-ttu-id="496f8-123">Kompletní příklad demonstruje použití obchodních objektů v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="496f8-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="496f8-124">V příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán na kolekci `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="496f8-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="496f8-125">Každý `Task` objekt má `AssignedTo` vlastnost, která označuje `Employee` objekt aktuálně přiřazená k této úloze.</span><span class="sxs-lookup"><span data-stu-id="496f8-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="496f8-126">`Assigned To` Sloupec zobrazuje `Name` přiřazené hodnota vlastnosti pro každý zaměstnanec, nebo "nepřiřazené", pokud `Task.AssignedTo` hodnota vlastnosti je `null`.</span><span class="sxs-lookup"><span data-stu-id="496f8-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="496f8-127">Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="496f8-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="496f8-128">Změna přiřazení v `Assigned To` odvodit sloupec podle výběru různých hodnot z rozevíracích seznamů nebo stisknutím klávesy CTRL + 0 v buňce pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="496f8-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="496f8-129">Klikněte na tlačítko `Generate Report` k zobrazení aktuálního přiřazení.</span><span class="sxs-lookup"><span data-stu-id="496f8-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="496f8-130">To ukazuje, že změna `Assigned To` sloupce automaticky aktualizuje `tasks` kolekce.</span><span class="sxs-lookup"><span data-stu-id="496f8-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="496f8-131">Klikněte na tlačítko `Request Status` tlačítka zavoláte `RequestStatus` metoda aktuálního `Employee` objekt pro tento řádek.</span><span class="sxs-lookup"><span data-stu-id="496f8-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="496f8-132">Tento příklad ukazuje, že vybraný objekt se úspěšně načetl.</span><span class="sxs-lookup"><span data-stu-id="496f8-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="496f8-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="496f8-133">Compiling the Code</span></span>  
 <span data-ttu-id="496f8-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="496f8-134">This example requires:</span></span>  
  
-   <span data-ttu-id="496f8-135">Odkazy na sestavení systému a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="496f8-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="496f8-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="496f8-136">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [<span data-ttu-id="496f8-137">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="496f8-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
