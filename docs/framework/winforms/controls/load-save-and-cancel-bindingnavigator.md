---
title: Přidání tlačítek načíst, Uložit a Storno do ovládacího prvku BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: ac862d163f1bd8b66f29160d836bc459e4bf4081
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745136"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="78d11-102">Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="78d11-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>

<span data-ttu-id="78d11-103"><xref:System.Windows.Forms.BindingNavigator> ovládací prvek je <xref:System.Windows.Forms.ToolStrip> ovládací prvek pro zvláštní účely, který je určen pro navigaci a manipulaci s ovládacími prvky formuláře, které jsou vázány na data.</span><span class="sxs-lookup"><span data-stu-id="78d11-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>

<span data-ttu-id="78d11-104">Vzhledem k tomu, že se jedná o ovládací prvek <xref:System.Windows.Forms.ToolStrip>, lze komponentu <xref:System.Windows.Forms.BindingNavigator> snadno upravit tak, aby zahrnovala další nebo alternativní příkazy pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="78d11-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>

<span data-ttu-id="78d11-105">V následujícím postupu je ovládací prvek <xref:System.Windows.Forms.TextBox> vázán na data a ovládací prvek <xref:System.Windows.Forms.ToolStrip> přidaný do formuláře se upraví tak, aby zahrnoval tlačítka načíst, Uložit a Storno.</span><span class="sxs-lookup"><span data-stu-id="78d11-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>

## <a name="add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="78d11-106">Přidání tlačítek načíst, Uložit a Storno do komponenty BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="78d11-106">Add load, save, and cancel buttons to the BindingNavigator component</span></span>

1. <span data-ttu-id="78d11-107">V aplikaci Visual Studio přidejte ovládací prvek <xref:System.Windows.Forms.TextBox> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="78d11-107">In Visual Studio, add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>

2. <span data-ttu-id="78d11-108">Vytvořte vazbu na <xref:System.Windows.Forms.BindingSource>, která je svázána se zdrojem dat.</span><span class="sxs-lookup"><span data-stu-id="78d11-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="78d11-109">V tomto příkladu je <xref:System.Windows.Forms.BindingSource> svázán s databází.</span><span class="sxs-lookup"><span data-stu-id="78d11-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>

3. <span data-ttu-id="78d11-110">Po vygenerování datové sady a adaptéru tabulky přetáhněte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="78d11-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>

4. <span data-ttu-id="78d11-111">Nastavte vlastnost <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> na <xref:System.Windows.Forms.BindingSource> ve formuláři, který je svázán s ovládacími prvky.</span><span class="sxs-lookup"><span data-stu-id="78d11-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>

5. <span data-ttu-id="78d11-112">Vyberte ovládací prvek <xref:System.Windows.Forms.BindingNavigator>.</span><span class="sxs-lookup"><span data-stu-id="78d11-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>

6. <span data-ttu-id="78d11-113">Klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), aby se zobrazil dialog **úlohy BindingNavigator** , a vyberte **Upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="78d11-113">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>

     <span data-ttu-id="78d11-114">Zobrazí se **Editor kolekce Items** .</span><span class="sxs-lookup"><span data-stu-id="78d11-114">The **Items Collection Editor** appears.</span></span>

7. <span data-ttu-id="78d11-115">V **editoru kolekce položek**proveďte následující:</span><span class="sxs-lookup"><span data-stu-id="78d11-115">In the **Items Collection Editor**, complete the following:</span></span>

    1. <span data-ttu-id="78d11-116">Přidejte <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky výběrem příslušného typu <xref:System.Windows.Forms.ToolStripItem> a kliknutím na tlačítko **Přidat** .</span><span class="sxs-lookup"><span data-stu-id="78d11-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>

    2. <span data-ttu-id="78d11-117">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Name%2A> pro tlačítka na **LoadButton**, **SaveButton**a **CancelButton**v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="78d11-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>

    3. <span data-ttu-id="78d11-118">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.Text%2A> pro tlačítka na **načíst**, **Uložit**a **Zrušit**.</span><span class="sxs-lookup"><span data-stu-id="78d11-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>

    4. <span data-ttu-id="78d11-119">Nastavte vlastnost <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> pro každé z tlačítek na **text**.</span><span class="sxs-lookup"><span data-stu-id="78d11-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="78d11-120">Alternativně můžete tuto vlastnost nastavit na hodnotu **Image** nebo **ImageAndText**a nastavit obrázek, který se má zobrazit ve vlastnosti <xref:System.Windows.Forms.ToolStripItem.Image%2A>.</span><span class="sxs-lookup"><span data-stu-id="78d11-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>

    5. <span data-ttu-id="78d11-121">Kliknutím na **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="78d11-121">Click **OK** to close the dialog box.</span></span> <span data-ttu-id="78d11-122">Tlačítka jsou přidána do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="78d11-122">The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>

8. <span data-ttu-id="78d11-123">Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="78d11-123">Right-click the form and choose **View Code**.</span></span>

9. <span data-ttu-id="78d11-124">V editoru kódu vyhledejte řádek kódu, který načte data do adaptéru tabulky.</span><span class="sxs-lookup"><span data-stu-id="78d11-124">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="78d11-125">Tento kód byl vygenerován při nastavení datové vazby v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="78d11-125">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="78d11-126">Kód by měl vypadat přibližně takto: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="78d11-126">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="78d11-127">Pravděpodobně bude v události <xref:System.Windows.Forms.Form.Load> formuláře.</span><span class="sxs-lookup"><span data-stu-id="78d11-127">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>

10. <span data-ttu-id="78d11-128">Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> **zátěžového** <xref:System.Windows.Forms.ToolStripButton>, kterou jste vytvořili dříve, a přesuňte do ní kód pro načtení dat.</span><span class="sxs-lookup"><span data-stu-id="78d11-128">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>

     <span data-ttu-id="78d11-129">Váš kód by teď měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="78d11-129">Your code should now look similar to the following:</span></span>

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

11. <span data-ttu-id="78d11-130">Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> **uloženého**<xref:System.Windows.Forms.ToolStripButton>, kterou jste vytvořili dříve, a napište kód pro aktualizaci dat v tabulce, ke které je ovládací prvek vázán.</span><span class="sxs-lookup"><span data-stu-id="78d11-130">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>

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
    > <span data-ttu-id="78d11-131">V některých případech již komponenta <xref:System.Windows.Forms.BindingNavigator> obsahuje tlačítko **Uložit** , ale Návrhář formulářů nevytvořil žádný kód.</span><span class="sxs-lookup"><span data-stu-id="78d11-131">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component already has a **Save** button, but no code has been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="78d11-132">V tomto případě můžete umístit předchozí kód do obslužné rutiny události <xref:System.Windows.Forms.ToolStripItem.Click> pro toto tlačítko místo vytvoření zcela nového tlačítka v <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="78d11-132">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="78d11-133">Toto tlačítko je ale ve výchozím nastavení zakázané, takže musíte nastavit vlastnost <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> tlačítka, aby `true`, aby správně fungovalo tlačítko.</span><span class="sxs-lookup"><span data-stu-id="78d11-133">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>

12. <span data-ttu-id="78d11-134">Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.ToolStripItem.Click> <xref:System.Windows.Forms.ToolStripButton> **zrušení** , kterou jste vytvořili dříve, a napište kód, který zruší všechny změny v zobrazeném datovém záznamu.</span><span class="sxs-lookup"><span data-stu-id="78d11-134">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>

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
    > <span data-ttu-id="78d11-135">Metoda <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> je vymezena na řádek dat.</span><span class="sxs-lookup"><span data-stu-id="78d11-135">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="78d11-136">Před přechodem na další záznam uložte všechny změny, které provedete při prohlížení tohoto jednotlivého záznamu.</span><span class="sxs-lookup"><span data-stu-id="78d11-136">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>

## <a name="see-also"></a><span data-ttu-id="78d11-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="78d11-137">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="78d11-138">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="78d11-138">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="78d11-139">Přehled komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="78d11-139">BindingSource Component Overview</span></span>](bindingsource-component-overview.md)
