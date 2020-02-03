---
title: Přístup k objektům v rozevíracím seznamu DataGridViewComboBoxCell
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746312"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="5cb9e-102">Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell</span><span class="sxs-lookup"><span data-stu-id="5cb9e-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="5cb9e-103">Stejně jako ovládací prvek <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy umožňují přidat libovolné objekty do jejich rozevíracích seznamů.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="5cb9e-104">Pomocí této funkce můžete reprezentovat komplexní stavy v rozevíracím seznamu, aniž byste museli ukládat odpovídající objekty v samostatné kolekci.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="5cb9e-105">Na rozdíl od ovládacího prvku <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.DataGridView> typy nemají vlastnost <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> pro načtení aktuálně vybraného objektu.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="5cb9e-106">Místo toho musíte nastavit vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> na název vlastnosti v obchodním objektu.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="5cb9e-107">Když uživatel provede výběr, určí vlastnost byznys objektu vlastnost <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="5cb9e-108">Chcete-li načíst obchodní objekt prostřednictvím hodnoty buňky, musí vlastnost `ValueMember` indikovat vlastnost, která vrací odkaz na samotný obchodní objekt.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="5cb9e-109">Proto pokud typ obchodního objektu není pod vaším ovládacím prvkem, je nutné přidat takovou vlastnost rozšířením typu prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="5cb9e-110">Následující postupy ukazují, jak naplnit rozevírací seznam pomocí obchodních objektů a načíst objekty pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="5cb9e-111">Přidání obchodních objektů do rozevíracího seznamu</span><span class="sxs-lookup"><span data-stu-id="5cb9e-111">To add business objects to the drop-down list</span></span>  
  
1. <span data-ttu-id="5cb9e-112">Vytvořte nový <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplňte jeho kolekci <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="5cb9e-113">Případně můžete nastavit vlastnost <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> sloupce na kolekci obchodních objektů.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="5cb9e-114">V takovém případě však nemůžete do rozevíracího seznamu přidat "Nepřiřazeno" bez vytvoření odpovídajícího podnikového objektu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <span data-ttu-id="5cb9e-115">Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="5cb9e-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> určuje vlastnost obchodního objektu, která se má zobrazit v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="5cb9e-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> určuje vlastnost, která vrací odkaz na obchodní objekt.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. <span data-ttu-id="5cb9e-118">Ujistěte se, že typ obchodního objektu obsahuje vlastnost, která vrací odkaz na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="5cb9e-119">Tato vlastnost musí být pojmenována s hodnotou přiřazenou <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="5cb9e-120">Načtení aktuálně vybraného obchodního objektu</span><span class="sxs-lookup"><span data-stu-id="5cb9e-120">To retrieve the currently selected business object</span></span>  
  
- <span data-ttu-id="5cb9e-121">Získat vlastnost <xref:System.Windows.Forms.DataGridViewCell.Value%2A> buňky a přetypovat ji na typ obchodního objektu.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="5cb9e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5cb9e-122">Example</span></span>  
 <span data-ttu-id="5cb9e-123">Kompletní příklad ukazuje použití obchodních objektů v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="5cb9e-124">V příkladu je ovládací prvek <xref:System.Windows.Forms.DataGridView> vázán na kolekci objektů `Task`.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="5cb9e-125">Každý objekt `Task` má vlastnost `AssignedTo`, která indikuje objekt `Employee` aktuálně přiřazený k této úloze.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="5cb9e-126">`Assigned To` sloupec zobrazuje hodnotu vlastnosti `Name` pro každého přiřazeného zaměstnance nebo "Nepřiřazeno", pokud je hodnota vlastnosti `Task.AssignedTo` `null`a.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="5cb9e-127">Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5cb9e-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="5cb9e-128">Změňte přiřazení ve sloupci `Assigned To` výběrem různých hodnot z rozevíracích seznamů nebo stisknutím kombinace kláves CTRL + 0 v buňce pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2. <span data-ttu-id="5cb9e-129">Kliknutím na `Generate Report` zobrazíte aktuální přiřazení.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="5cb9e-130">To ukazuje, že změna ve sloupci `Assigned To` automaticky aktualizuje kolekci `tasks`.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3. <span data-ttu-id="5cb9e-131">Klikněte na `Request Status` tlačítko a zavolejte metodu `RequestStatus` aktuálního objektu `Employee` pro daný řádek.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="5cb9e-132">To ukazuje, že vybraný objekt byl úspěšně načten.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cb9e-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5cb9e-133">Compiling the Code</span></span>  
 <span data-ttu-id="5cb9e-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5cb9e-134">This example requires:</span></span>  
  
- <span data-ttu-id="5cb9e-135">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="5cb9e-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb9e-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cb9e-136">See also</span></span>

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
- [<span data-ttu-id="5cb9e-137">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5cb9e-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
