---
title: "Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell"
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
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0fac2e73e76ad49a5b1ce6942f3ae2b4c0584e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="ff5ae-102">Postupy: Přístup k objektům v rozevíracím seznamu Windows Forms DataGridViewComboBoxCell</span><span class="sxs-lookup"><span data-stu-id="ff5ae-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="ff5ae-103">Podobně jako <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a <xref:System.Windows.Forms.DataGridViewComboBoxCell> typy povolit, můžete přidat libovolné objekty do jejich rozevírací seznamy.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="ff5ae-104">Pomocí této funkce může představovat komplexní stavů v rozevíracím seznamu bez nutnosti ukládat odpovídající objekty v samostatné kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="ff5ae-105">Na rozdíl od <xref:System.Windows.Forms.ComboBox> ovládací prvek, <xref:System.Windows.Forms.DataGridView> typy nemají <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> vlastnost pro načítání aktuálně vybraného objektu.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="ff5ae-106">Místo toho je nutné nastavit <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> vlastnost na název vlastnosti v objektu vaší firmy.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="ff5ae-107">Když uživatel provede výběr, uvedené vlastnost objektu obchodní nastaví buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="ff5ae-108">K načtení objektu obchodní prostřednictvím hodnotu buňky `ValueMember` vlastnost musí označovat vlastnost, která vrátí odkaz na objekt obchodní sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="ff5ae-109">Proto pokud typ objektu obchodní není ve vaší kontrole, musíte přidat taková vlastnost rozšířením typu prostřednictvím dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="ff5ae-110">Následující postupy ukazují, jak k naplnění rozevíracího seznamu s obchodní objekty a načtení objektů prostřednictvím buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="ff5ae-111">Chcete-li přidat objekty obchodní do rozevíracího seznamu</span><span class="sxs-lookup"><span data-stu-id="ff5ae-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="ff5ae-112">Vytvořte novou <xref:System.Windows.Forms.DataGridViewComboBoxColumn> a naplnit její <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="ff5ae-113">Alternativně můžete nastavit sloupec <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> vlastnost ke kolekci obchodních objektů.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="ff5ae-114">V takovém případě však nelze přidáte "nepřiřazené" do rozevíracího seznamu bez vytvoření odpovídající obchodní objekt v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="ff5ae-115">Nastavte <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> a <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="ff5ae-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>Určuje vlastnost objektu obchodní zobrazíte v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="ff5ae-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>Určuje vlastnost, která vrátí odkaz na objekt firmy.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="ff5ae-118">Ujistěte se, že vaše obchodní typ objektu obsahuje vlastnosti, která vrátí odkaz na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="ff5ae-119">Tato vlastnost musí mít název s hodnotu přiřazenou <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="ff5ae-120">Načíst objekt aktuálně vybraného firmy</span><span class="sxs-lookup"><span data-stu-id="ff5ae-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="ff5ae-121">Získat buňky <xref:System.Windows.Forms.DataGridViewCell.Value%2A> vlastnost a přetypovat na typ objektu firmy.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="ff5ae-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff5ae-122">Example</span></span>  
 <span data-ttu-id="ff5ae-123">Úplný příklad ukazuje použití obchodních objektů v rozevíracím seznamu.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="ff5ae-124">V příkladu <xref:System.Windows.Forms.DataGridView> ovládací prvek vázán ke kolekci `Task` objekty.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="ff5ae-125">Každý `Task` objekt má `AssignedTo` vlastnost, která určuje, `Employee` objektu, které jsou přiřazeny k této úlohy.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="ff5ae-126">`Assigned To` Sloupec zobrazuje `Name` přiřazena hodnota vlastnosti pro každý zaměstnanec, nebo "nepřiřazené", pokud `Task.AssignedTo` hodnota vlastnosti je `null`.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="ff5ae-127">Chcete-li zobrazit chování tohoto příkladu, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="ff5ae-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="ff5ae-128">Změna přiřazení v `Assigned To` sloupec výběrem různé hodnoty z rozevíracího seznamu nebo kombinace kláves CTRL + 0 v buňce pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="ff5ae-129">Klikněte na tlačítko `Generate Report` zobrazit aktuální přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="ff5ae-130">Tento příklad ukazuje, který změnu `Assigned To` sloupec automaticky aktualizuje `tasks` kolekce.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="ff5ae-131">Klikněte na tlačítko `Request Status` tlačítko volání `RequestStatus` metoda aktuálního `Employee` objektu na příslušném řádku.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="ff5ae-132">Tento příklad ukazuje úspěšně načetl vybraný objekt.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff5ae-133">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ff5ae-133">Compiling the Code</span></span>  
 <span data-ttu-id="ff5ae-134">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ff5ae-134">This example requires:</span></span>  
  
-   <span data-ttu-id="ff5ae-135">Odkazy na systém a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="ff5ae-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5ae-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff5ae-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="ff5ae-137">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="ff5ae-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
