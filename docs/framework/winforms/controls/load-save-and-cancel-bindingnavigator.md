---
title: 'Postupy: Přidávání tlačítek Načíst, Uložit a Zrušit do ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 52d4fc32836a5d20bd99d8ebfd3119c761376e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098712"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="ae970-102">Postupy: Přidávání tlačítek Načíst, Uložit a Zrušit do ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="ae970-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="ae970-103"><xref:System.Windows.Forms.BindingNavigator> Ovládací prvek se speciálním účelem <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je určený pro navigaci a manipulaci se ovládací prvky na formuláři, které jsou vázány na data.</span><span class="sxs-lookup"><span data-stu-id="ae970-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="ae970-104">Protože se jedná <xref:System.Windows.Forms.ToolStrip> ovládací prvek, <xref:System.Windows.Forms.BindingNavigator> součásti můžete snadno upravit tak, aby patří další nebo alternativní příkazy pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="ae970-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="ae970-105">V následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán na data a <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je přidán do formuláře je upravit tak, aby zahrnout načíst, uložit a stornovací tlačítka.</span><span class="sxs-lookup"><span data-stu-id="ae970-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="ae970-106">Chcete-li přidat zatížení, uložte a stornovací tlačítka na komponentu BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="ae970-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="ae970-107">Přidat <xref:System.Windows.Forms.TextBox> ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ae970-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="ae970-108">Vytvořte mu vazbu k <xref:System.Windows.Forms.BindingSource>, který je svázán se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="ae970-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="ae970-109">V tomto příkladu <xref:System.Windows.Forms.BindingSource> je vázán na databázi.</span><span class="sxs-lookup"><span data-stu-id="ae970-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="ae970-110">Po vygenerování adaptér datová sada a tabulky, přetáhněte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="ae970-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="ae970-111">Nastavte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost <xref:System.Windows.Forms.BindingSource> ve formuláři, který je vázán k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="ae970-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="ae970-112">Vyberte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ae970-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="ae970-113">Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) proto **BindingNavigator úlohy** dialogové okno se zobrazí a vyberte **upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="ae970-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="ae970-114">**Editor kolekce položek** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="ae970-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="ae970-115">V **Editor kolekce položek**, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="ae970-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="ae970-116">Přidat <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky tak, že vyberete příslušný typ <xref:System.Windows.Forms.ToolStripItem> a kliknete **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ae970-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="ae970-117">Nastavte <xref:System.Windows.Forms.ToolStripItem.Name%2A> vlastnost tlačítek na hodnotu **LoadButton**, **SaveButton**, a **CancelButton**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="ae970-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="ae970-118">Nastavte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost tlačítek na hodnotu **zatížení**, **Uložit**, a **zrušit**.</span><span class="sxs-lookup"><span data-stu-id="ae970-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>  
  
    4.  <span data-ttu-id="ae970-119">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost pro každý z tlačítka **Text**.</span><span class="sxs-lookup"><span data-stu-id="ae970-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="ae970-120">Alternativně nastavte tuto vlastnost na **Image** nebo **ImageAndText**a nastavit obrázek, který se zobrazí v <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae970-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="ae970-121">Klikněte na tlačítko **OK** zavřete dialogové okno. Tlačítka jsou přidány do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ae970-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="ae970-122">Klikněte pravým tlačítkem na formuláři a zvolte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="ae970-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="ae970-123">V editoru kódu vyhledejte řádek kódu, který načte data do tabulky adaptéru.</span><span class="sxs-lookup"><span data-stu-id="ae970-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="ae970-124">Tento kód se vygeneroval při nastavení datové vazby v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="ae970-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="ae970-125">Kód by měl vypadat přibližně takto: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="ae970-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="ae970-126">Bude většinu pravděpodobně v formuláře <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="ae970-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="ae970-127">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zatížení** <xref:System.Windows.Forms.ToolStripButton> jste vytvořili dříve a přesuňte tento kód načítání dat do něj.</span><span class="sxs-lookup"><span data-stu-id="ae970-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="ae970-128">Váš kód by teď měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="ae970-128">Your code should now look similar to the following:</span></span>  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. <span data-ttu-id="ae970-129">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **Uložit** <xref:System.Windows.Forms.ToolStripButton> jste vytvořili dříve a napsat kód k aktualizaci dat v ovládacím prvku tabulka je vázána na.</span><span class="sxs-lookup"><span data-stu-id="ae970-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="ae970-130">V některých případech <xref:System.Windows.Forms.BindingNavigator> již komponenty budou **Uložit** tlačítko, ale žádný kód bude byly vytvořeny v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="ae970-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a **Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="ae970-131">V takovém případě můžete umístit v předchozím kódu <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro toto tlačítko, místo vytvoření zcela nové tlačítko na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="ae970-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="ae970-132">Nicméně je tlačítko neaktivní ve výchozím nastavení, proto musíte nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost tlačítka `true` má tlačítko funkce správně.</span><span class="sxs-lookup"><span data-stu-id="ae970-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>
  
12. <span data-ttu-id="ae970-133">Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.ToolStripItem.Click> událost **zrušit** <xref:System.Windows.Forms.ToolStripButton> vytvořené dříve a napsat kód, který zrušit všechny změny na datový záznam, který se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="ae970-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ae970-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda působí na řádek dat.</span><span class="sxs-lookup"><span data-stu-id="ae970-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="ae970-135">Uložte všechny změny, které pronesete při zobrazení jednotlivých záznamu před přechodu na další záznam.</span><span class="sxs-lookup"><span data-stu-id="ae970-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae970-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae970-136">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="ae970-137">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="ae970-137">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="ae970-138">BindingSource – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="ae970-138">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
