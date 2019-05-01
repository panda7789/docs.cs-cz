---
title: Rozšiřitelnost mřížky vlastností – ukázky WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: f1cb64cb10e8d88359e8f94b57602ab127314cff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004871"
---
# <a name="property-grid-extensibility"></a><span data-ttu-id="828e4-102">Rozšiřitelnost mřížky vlastností</span><span class="sxs-lookup"><span data-stu-id="828e4-102">Property grid extensibility</span></span>

<span data-ttu-id="828e4-103">Vývojář můžete přizpůsobit mřížkou, který se zobrazí při výběru v návrháři pro danou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="828e4-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="828e4-104">To můžete udělat vytvořit bohaté možnosti úprav.</span><span class="sxs-lookup"><span data-stu-id="828e4-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="828e4-105">Tato ukázka předvádí, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="828e4-105">This sample shows how this can be done.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="828e4-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="828e4-106">Demonstrates</span></span>

<span data-ttu-id="828e4-107">Rozšiřitelnost mřížky vlastností Návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="828e4-107">Workflow designer property grid extensibility.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="828e4-108">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="828e4-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="828e4-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="828e4-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="828e4-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="828e4-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="828e4-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="828e4-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a><span data-ttu-id="828e4-112">Diskuse</span><span class="sxs-lookup"><span data-stu-id="828e4-112">Discussion</span></span>

<span data-ttu-id="828e4-113">K rozšíření mřížkou, vývojář má možností pro přizpůsobení vzhledu vložené editor mřížky vlastností nebo zadejte, který se zobrazí dialogové okno pro pokročilejší úpravy plochu.</span><span class="sxs-lookup"><span data-stu-id="828e4-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="828e4-114">Existují dva různé editory jsme vám ukázali v této ukázce; editor vložené a editor dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="828e4-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>

## <a name="inline-editor"></a><span data-ttu-id="828e4-115">Vložené editoru</span><span class="sxs-lookup"><span data-stu-id="828e4-115">Inline editor</span></span>

<span data-ttu-id="828e4-116">Vložená ukázka editoru ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="828e4-116">The inline editor sample demonstrates the following:</span></span>

- <span data-ttu-id="828e4-117">Umožňuje vytvořit typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="828e4-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>

- <span data-ttu-id="828e4-118">V konstruktoru <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnota se nastaví pomocí datové šablony Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="828e4-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a Windows Presentation Foundation (WPF) data template.</span></span> <span data-ttu-id="828e4-119">To může být vázaný na šablonu XAML, ale v této ukázce kódu slouží k inicializaci datové vazby.</span><span class="sxs-lookup"><span data-stu-id="828e4-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>

- <span data-ttu-id="828e4-120">Šablony má kontext dat objektu <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> vykreslen v mřížce vlastností položky.</span><span class="sxs-lookup"><span data-stu-id="828e4-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="828e4-121">Poznámka: v následujícím kódu (z CustomInlineEditor.cs), který tento kontext pak vytvoří vazbu na `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="828e4-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>

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

- <span data-ttu-id="828e4-122">Protože aktivity a návrháři jsou ve stejném sestavení, můžete registraci atributy návrháře aktivit provést v statický konstruktor aktivity, jak je znázorněno v následujícím příkladu od SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="828e4-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a><span data-ttu-id="828e4-123">Editor dialogových oken</span><span class="sxs-lookup"><span data-stu-id="828e4-123">Dialog editor</span></span>

<span data-ttu-id="828e4-124">Ukázka editoru dialogového okna ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="828e4-124">The dialog editor sample demonstrates the following:</span></span>

1. <span data-ttu-id="828e4-125">Umožňuje vytvořit typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span><span class="sxs-lookup"><span data-stu-id="828e4-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>

2. <span data-ttu-id="828e4-126">Nastaví <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnotu v konstruktoru s [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] datové šablony.</span><span class="sxs-lookup"><span data-stu-id="828e4-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="828e4-127">To je možné vytvořit v XAML, ale v této ukázce, tím se vytvoří v kódu.</span><span class="sxs-lookup"><span data-stu-id="828e4-127">This can be created in XAML, but in this sample, this is created in code.</span></span>

3. <span data-ttu-id="828e4-128">Šablony má kontext dat objektu <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> vykreslen v mřížce vlastností položky.</span><span class="sxs-lookup"><span data-stu-id="828e4-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="828e4-129">V následujícím kódu, poté vytvoří vazbu `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="828e4-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="828e4-130">Je důležité zahrnout také <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> poskytnout tlačítka, které vyvolá dialogové okno v FilePickerEditor.cs.</span><span class="sxs-lookup"><span data-stu-id="828e4-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>

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

4. <span data-ttu-id="828e4-131">Přepsání <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> metoda v typu návrháře pro zpracování zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="828e4-131">Overrides the <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="828e4-132">V této ukázce základní <xref:System.Windows.Forms.FileDialog> se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="828e4-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>

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

5. <span data-ttu-id="828e4-133">Protože aktivity a návrháři jsou ve stejném sestavení, můžete registraci atributy návrháře aktivit provést v statický konstruktor aktivity, jak je znázorněno v následujícím příkladu od SimpleCodeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="828e4-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="828e4-134">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="828e4-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="828e4-135">Sestavte řešení a pak otevřete Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="828e4-135">Build the solution, and then open Workflow1.xaml.</span></span>

2. <span data-ttu-id="828e4-136">Přetáhněte **SimpleCodeActivity** z panelu nástrojů do plátna návrháře.</span><span class="sxs-lookup"><span data-stu-id="828e4-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>

3. <span data-ttu-id="828e4-137">Klikněte na tlačítko **SimpleCodeActivity** a pak otevřete mřížky vlastností níž se nachází na ovládacím prvku posuvník a soubor výběru ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="828e4-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="828e4-138">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="828e4-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="828e4-139">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="828e4-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="828e4-140">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="828e4-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="828e4-141">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="828e4-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`