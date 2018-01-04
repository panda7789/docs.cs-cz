---
title: "Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator"
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
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd45b33fb1f99c280e126b9e601692a85da5dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="807cb-102">Postupy: Přidávání tlačítek Načíst, Uložit a Storno do ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="807cb-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="807cb-103"><xref:System.Windows.Forms.BindingNavigator> Ovládací prvek je zvláštní účely <xref:System.Windows.Forms.ToolStrip> ovládací prvek, který je určený pro navigaci a manipulace s nimi ovládacích prvků formuláře, které jsou vázané na data.</span><span class="sxs-lookup"><span data-stu-id="807cb-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="807cb-104">Protože je <xref:System.Windows.Forms.ToolStrip> ovládací prvek, <xref:System.Windows.Forms.BindingNavigator> součást můžete snadno upravit tak, aby zahrnout další nebo alternativní příkazy pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="807cb-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="807cb-105">V následujícím postupu <xref:System.Windows.Forms.TextBox> ovládací prvek vázán k datům a <xref:System.Windows.Forms.ToolStrip> zahrnout zatížení, uložit a Storno tlačítka se mění ovládací prvek, který je přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="807cb-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="807cb-106">Chcete-li přidat zatížení, uložte a stornovací tlačítka pro komponentu BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="807cb-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="807cb-107">Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="807cb-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="807cb-108">Vytvořte mu vazbu k <xref:System.Windows.Forms.BindingSource>, který je vázán na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="807cb-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="807cb-109">V tomto příkladu <xref:System.Windows.Forms.BindingSource> je vázán k databázi.</span><span class="sxs-lookup"><span data-stu-id="807cb-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="807cb-110">Po vygenerování adaptér datovou sadu a tabulky, přetáhněte ji <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="807cb-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="807cb-111">Nastavte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost, která má <xref:System.Windows.Forms.BindingSource> na formuláři, který je vázaný na ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="807cb-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="807cb-112">Vyberte <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="807cb-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="807cb-113">Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) proto **BindingNavigator úlohy** se zobrazí dialogové okno a vybrat **upravit položky**.</span><span class="sxs-lookup"><span data-stu-id="807cb-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="807cb-114">**Editor kolekce položek** se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="807cb-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="807cb-115">V **Editor kolekce položek**, proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="807cb-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="807cb-116">Přidat <xref:System.Windows.Forms.ToolStripSeparator> a tři <xref:System.Windows.Forms.ToolStripButton> položky výběrem odpovídající typ <xref:System.Windows.Forms.ToolStripItem> a kliknutím **přidat** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="807cb-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="807cb-117">Nastavte <xref:System.Windows.Forms.ToolStripItem.Name%2A> vlastnost tlačítek na**LoadButton**,**SaveButton**, a**CancelButton**, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="807cb-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to**LoadButton**,**SaveButton**, and**CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="807cb-118">Nastavte <xref:System.Windows.Forms.ToolStripItem.Text%2A> vlastnost tlačítek na**zatížení** `,` **Uložit**, a**zrušit**.</span><span class="sxs-lookup"><span data-stu-id="807cb-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to**Load**`,` **Save**, and**Cancel**.</span></span>  
  
    4.  <span data-ttu-id="807cb-119">Nastavte <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> vlastnost pro každou z tlačítka na**Text**.</span><span class="sxs-lookup"><span data-stu-id="807cb-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to**Text**.</span></span> <span data-ttu-id="807cb-120">Alternativně nastavte tuto vlastnost na**Image**nebo**ImageAndText**a nastavte obrázek, který se zobrazí v <xref:System.Windows.Forms.ToolStripItem.Image%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="807cb-120">Alternatively, you can set this property to**Image**or**ImageAndText**and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="807cb-121">Klikněte na tlačítko **OK** zavřete dialogové okno. Tlačítka se přidají do <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="807cb-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="807cb-122">Klikněte pravým tlačítkem na formulář a zvolte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="807cb-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="807cb-123">V editoru kódu najděte řádek kódu, který načte data do tabulky adaptéru.</span><span class="sxs-lookup"><span data-stu-id="807cb-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="807cb-124">Tento kód byl vygenerován při nastavování datové vazby v kroku 2.</span><span class="sxs-lookup"><span data-stu-id="807cb-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="807cb-125">Kód by mělo být podobné následujícímu: `TableAdapterName.Fill(DataSetName.TableName)`.</span><span class="sxs-lookup"><span data-stu-id="807cb-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="807cb-126">Zruší většinu pravděpodobně v formuláře <xref:System.Windows.Forms.Form.Load> událostí.</span><span class="sxs-lookup"><span data-stu-id="807cb-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="807cb-127">Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události**zatížení** <xref:System.Windows.Forms.ToolStripButton> jste dříve vytvořili a přesunout tento kód načítání dat do ní.</span><span class="sxs-lookup"><span data-stu-id="807cb-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Load**<xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="807cb-128">Váš kód by teď měl vypadat podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="807cb-128">Your code should now look similar to the following:</span></span>  
  
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
  
11. <span data-ttu-id="807cb-129">Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události **Uložit** <xref:System.Windows.Forms.ToolStripButton> jste předtím vytvořili, a je svázaná zápisu kódu aktualizace dat v tabulce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="807cb-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
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
    >  <span data-ttu-id="807cb-130">V některých případech <xref:System.Windows.Forms.BindingNavigator> součást se už**Uložit** tlačítko, ale žádný kód bude byla vygenerována Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="807cb-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a**Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="807cb-131">V takovém případě můžete umístit předchozí kód <xref:System.Windows.Forms.ToolStripItem.Click> obslužné rutiny události pro toto tlačítko, místo vytvoření na úplně novou tlačítko <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="807cb-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="807cb-132">Tlačítko je však zakázána ve výchozím nastavení, takže je třeba nastavit <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost na tlačítko `true` tak, aby měl funkce tlačítko správně.</span><span class="sxs-lookup"><span data-stu-id="807cb-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>  
  
12. <span data-ttu-id="807cb-133">Vytvoření obslužné rutiny události pro <xref:System.Windows.Forms.ToolStripItem.Click> události**zrušit** <xref:System.Windows.Forms.ToolStripButton> jste dříve vytvořili a napsat kód pro zrušit všechny provedené změny k záznamu dat, který se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="807cb-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the**Cancel**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
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
    >  <span data-ttu-id="807cb-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Metoda je vymezen na řádek dat.</span><span class="sxs-lookup"><span data-stu-id="807cb-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="807cb-135">Uložte změny provedené při zobrazení jednotlivých záznamů před přejdete na další záznam.</span><span class="sxs-lookup"><span data-stu-id="807cb-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807cb-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="807cb-136">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="807cb-137">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="807cb-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="807cb-138">Přehled komponenty BindingSource</span><span class="sxs-lookup"><span data-stu-id="807cb-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
