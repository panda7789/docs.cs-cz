---
title: Rozšiřitelnost mřížky vlastností – ukázka WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: 130d8702795bccf0d5f28b5c0940bd7c25be3556
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715607"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="e3dad-102">Rozšíření mřížky vlastností</span><span class="sxs-lookup"><span data-stu-id="e3dad-102">Property grid extensibility</span></span>

<span data-ttu-id="e3dad-103">Vývojář může přizpůsobit mřížku vlastností, která se zobrazí při výběru dané aktivity v návrháři.</span><span class="sxs-lookup"><span data-stu-id="e3dad-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="e3dad-104">To se dá udělat, aby se vytvořilo prostředí s bohatou úpravou.</span><span class="sxs-lookup"><span data-stu-id="e3dad-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="e3dad-105">Tato ukázka ukazuje, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="e3dad-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e3dad-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="e3dad-106">Demonstrates</span></span>

<span data-ttu-id="e3dad-107">Rozšiřitelnost mřížky vlastností návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e3dad-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3dad-108">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e3dad-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3dad-109">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e3dad-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e3dad-110">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="e3dad-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3dad-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e3dad-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="e3dad-112">Účely</span><span class="sxs-lookup"><span data-stu-id="e3dad-112">Discussion</span></span>

<span data-ttu-id="e3dad-113">Chcete-li rozšířit mřížku vlastností, vývojář obsahuje možnosti přizpůsobení vloženého vzhledu editoru mřížky vlastností nebo poskytnutí dialogového okna, které se zobrazí pro pokročilejší editační plochu.</span><span class="sxs-lookup"><span data-stu-id="e3dad-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="e3dad-114">V této ukázce jsou znázorněny dva různé editory. vložený Editor a editor dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="e3dad-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="e3dad-115">Vložený Editor</span><span class="sxs-lookup"><span data-stu-id="e3dad-115">Inline editor</span></span>

<span data-ttu-id="e3dad-116">Ukázka vloženého editoru znázorňuje následující:</span><span class="sxs-lookup"><span data-stu-id="e3dad-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="e3dad-117">Vytvoří typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="e3dad-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="e3dad-118">V konstruktoru je hodnota <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> nastavena pomocí šablony dat Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e3dad-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="e3dad-119">Tato možnost může být vázána na šablonu XAML, ale v této ukázce se pro inicializaci datové vazby používá kód.</span><span class="sxs-lookup"><span data-stu-id="e3dad-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="e3dad-120">Datová šablona má kontext dat <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky vykreslené v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="e3dad-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="e3dad-121">Všimněte si, že v následujícím kódu (z CustomInlineEditor.cs) se tento kontext váže k vlastnosti `Value`.</span><span class="sxs-lookup"><span data-stu-id="e3dad-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

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

- <span data-ttu-id="e3dad-122">Vzhledem k tomu, že aktivita a Návrhář jsou ve stejném sestavení, probíhá registrace atributů návrháře aktivit ve statickém konstruktoru samotné aktivity, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="e3dad-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="e3dad-123">Editor dialogových oken</span><span class="sxs-lookup"><span data-stu-id="e3dad-123">Dialog editor</span></span>

<span data-ttu-id="e3dad-124">Ukázka v editoru dialogových oken ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="e3dad-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="e3dad-125">Vytvoří typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="e3dad-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="e3dad-126">Nastaví hodnotu <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> v konstruktoru pomocí šablony dat WPF.</span><span class="sxs-lookup"><span data-stu-id="e3dad-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a WPF data template.</span></span> <span data-ttu-id="e3dad-127">To lze vytvořit v jazyce XAML, ale v této ukázce je vytvořena v kódu.</span><span class="sxs-lookup"><span data-stu-id="e3dad-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="e3dad-128">Datová šablona má kontext dat <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky vykreslené v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="e3dad-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="e3dad-129">V následujícím kódu se pak vytvoří vazba na vlastnost `Value`.</span><span class="sxs-lookup"><span data-stu-id="e3dad-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="e3dad-130">Je důležité také zahrnout <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> k poskytnutí tlačítka, které vyvolává dialog v FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="e3dad-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

    ```csharp
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

4. <span data-ttu-id="e3dad-131">Přepíše metodu <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> v typu návrháře pro zpracování zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="e3dad-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="e3dad-132">V této ukázce se zobrazuje základní <xref:System.Windows.Forms.FileDialog>.</span><span class="sxs-lookup"><span data-stu-id="e3dad-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. <span data-ttu-id="e3dad-133">Vzhledem k tomu, že aktivita a Návrhář jsou ve stejném sestavení, probíhá registrace atributů návrháře aktivit ve statickém konstruktoru samotné aktivity, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="e3dad-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3dad-134">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e3dad-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e3dad-135">Sestavte řešení a pak otevřete Workflow1. XAML.</span><span class="sxs-lookup"><span data-stu-id="e3dad-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="e3dad-136">Přetáhněte **SimpleCodeActivity** z panelu nástrojů na plátno návrháře.</span><span class="sxs-lookup"><span data-stu-id="e3dad-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="e3dad-137">Klikněte na **SimpleCodeActivity** a pak otevřete mřížku vlastností, kde je ovládací prvek posuvníku a ovládací prvek pro výdej souboru.</span><span class="sxs-lookup"><span data-stu-id="e3dad-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e3dad-138">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e3dad-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3dad-139">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e3dad-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e3dad-140">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="e3dad-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3dad-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e3dad-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
