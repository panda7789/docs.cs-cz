---
title: Vlastnost Extensibliity mřížky
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9356e30a8b2d53a149e58f52f21fa6626dff0a75
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="property-grid-extensibliity"></a><span data-ttu-id="ba1ef-102">Vlastnost Extensibliity mřížky</span><span class="sxs-lookup"><span data-stu-id="ba1ef-102">Property Grid Extensibliity</span></span>
<span data-ttu-id="ba1ef-103">Vývojář může přizpůsobit mřížku vlastností, které se zobrazí, pokud je vybrána danou aktivitu v návrháři.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="ba1ef-104">To lze provést pro vytvoření bohaté úpravy prostředí.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="ba1ef-105">Tento příklad ukazuje, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-105">This sample shows how this can be done.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ba1ef-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="ba1ef-106">Demonstrates</span></span>  
 <span data-ttu-id="ba1ef-107">Rozšíření mřížky vlastnosti Návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-107">Workflow designer property grid extensibility.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba1ef-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba1ef-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ba1ef-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba1ef-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba1ef-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a><span data-ttu-id="ba1ef-112">Diskusní</span><span class="sxs-lookup"><span data-stu-id="ba1ef-112">Discussion</span></span>  
 <span data-ttu-id="ba1ef-113">Pokud chcete rozšířit mřížku vlastností, má vývojář možností pro přizpůsobení vzhledu vložené do editoru mřížky vlastnosti, nebo poskytněte dialog, který se zobrazí pro pokročilejší prostor pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="ba1ef-114">Existují dva různé editory předvedená v této ukázce; vložené editoru a editor dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>  
  
## <a name="inline-editor"></a><span data-ttu-id="ba1ef-115">Vložené editoru</span><span class="sxs-lookup"><span data-stu-id="ba1ef-115">Inline Editor</span></span>  
 <span data-ttu-id="ba1ef-116">Ukázka editor vložené ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="ba1ef-116">The inline editor sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="ba1ef-117">Vytvoří typ, který je odvozen od <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>  
  
-   <span data-ttu-id="ba1ef-118">V konstruktoru <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnota je nastavena pomocí šablony data Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ba1ef-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="ba1ef-119">To může být vázaný na šablonu XAML, ale v této ukázce kódu slouží k inicializaci datové vazby.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>  
  
-   <span data-ttu-id="ba1ef-120">Šablona dat má kontext dat z <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky v tabulce vlastností.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="ba1ef-121">Poznámka: v následujícím kódu (z CustomInlineEditor.cs), která tento kontext pak sváže `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>  
  
    ```csharp  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));  
    Binding sliderBinding = new Binding("Value");  
    sliderBinding.Mode = BindingMode.TwoWay;  
    slider.SetValue(Slider.MinimumProperty, 0.0);  
    slider.SetValue(Slider.MaximumProperty, 100.0);  
    slider.SetValue(Slider.ValueProperty, sliderBinding);  
    stack.AppendChild(slider);  
    ```  
  
-   <span data-ttu-id="ba1ef-122">Protože jsou ve stejném sestavení aktivity a návrháře, registrace atributů Návrhář aktivity lze provádět statického konstruktoru aktivity samostatně, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a><span data-ttu-id="ba1ef-123">Editor dialogových oken</span><span class="sxs-lookup"><span data-stu-id="ba1ef-123">Dialog Editor</span></span>  
 <span data-ttu-id="ba1ef-124">Dialogové okno editor ukázku ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="ba1ef-124">The dialog editor sample demonstrates the following:</span></span>  
  
1.  <span data-ttu-id="ba1ef-125">Vytvoří typ, který je odvozen od <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>  
  
2.  <span data-ttu-id="ba1ef-126">Nastaví <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnotu v konstruktoru s [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] datová šablona.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="ba1ef-127">To lze vytvořit v jazyce XAML, ale v této ukázce je vytvořena v kódu.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-127">This can be created in XAML, but in this sample, this is created in code.</span></span>  
  
3.  <span data-ttu-id="ba1ef-128">Šablona dat má kontext dat z <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky v tabulce vlastností.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="ba1ef-129">V následujícím kódu, to pak váže `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="ba1ef-130">Je důležité zahrnout také <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zajistit tlačítko vyvolá dialogové okno ve FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>  
  
    ```  
    this.InlineEditorTemplate = new DataTemplate();  
  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);  
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));  
    Binding labelBinding = new Binding("Value");  
    label.SetValue(Label.ContentProperty, labelBinding);  
    label.SetValue(Label.MaxWidthProperty, 90.0);  
  
    stack.AppendChild(label);  
  
    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));  
  
    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);  
  
    stack.AppendChild(editModeSwitch);  
  
    this.InlineEditorTemplate.VisualTree = stack;  
    ```  
  
4.  <span data-ttu-id="ba1ef-131">Přepsání <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` metoda v návrháře typu pro zpracování zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-131">Overrides the <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="ba1ef-132">V této ukázce základní <xref:System.Windows.Forms.FileDialog> se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="ba1ef-133">Protože jsou ve stejném sestavení aktivity a návrháře, registrace atributů Návrhář aktivity lze provádět statického konstruktoru aktivity samostatně, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ba1ef-134">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ba1ef-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ba1ef-135">Sestavte řešení a pak otevřete Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-135">Build the solution, and then open Workflow1.xaml.</span></span>  
  
2.  <span data-ttu-id="ba1ef-136">Přetáhněte **SimpleCodeActivity** z panelu nástrojů do plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>  
  
3.  <span data-ttu-id="ba1ef-137">Klikněte **SimpleCodeActivity** a pak otevřete mřížku vlastností, kde je ovládací prvek typu jezdec a soubor výběr ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ba1ef-138">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ba1ef-139">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ba1ef-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ba1ef-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ba1ef-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ba1ef-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
