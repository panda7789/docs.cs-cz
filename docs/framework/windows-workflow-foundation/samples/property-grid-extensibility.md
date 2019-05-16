---
title: Rozšiřitelnost mřížky vlastností – ukázky WF
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: d22b6e21fbf2d5deb4d47fce683553378e990000
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65637686"
---
# <a name="property-grid-extensibility"></a>Rozšiřitelnost mřížky vlastností

Vývojář můžete přizpůsobit mřížkou, který se zobrazí při výběru v návrháři pro danou aktivitu. To můžete udělat vytvořit bohaté možnosti úprav. Tato ukázka předvádí, jak to lze provést.

## <a name="demonstrates"></a>Demonstruje

Rozšiřitelnost mřížky vlastností Návrháře pracovního postupu.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Diskuse

K rozšíření mřížkou, vývojář má možností pro přizpůsobení vzhledu vložené editor mřížky vlastností nebo zadejte, který se zobrazí dialogové okno pro pokročilejší úpravy plochu. Existují dva různé editory jsme vám ukázali v této ukázce; editor vložené a editor dialogového okna.

## <a name="inline-editor"></a>Vložené editoru

Vložená ukázka editoru ukazuje následující:

- Umožňuje vytvořit typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.

- V konstruktoru <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnota se nastaví pomocí datové šablony Windows Presentation Foundation (WPF). To může být vázaný na šablonu XAML, ale v této ukázce kódu slouží k inicializaci datové vazby.

- Šablony má kontext dat objektu <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> vykreslen v mřížce vlastností položky. Poznámka: v následujícím kódu (z CustomInlineEditor.cs), který tento kontext pak vytvoří vazbu na `Value` vlastnost.

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

- Protože aktivity a návrháři jsou ve stejném sestavení, můžete registraci atributy návrháře aktivit provést v statický konstruktor aktivity, jak je znázorněno v následujícím příkladu od SimpleCodeActivity.cs.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a>Editor dialogových oken

Ukázka editoru dialogového okna ukazuje následující:

1. Umožňuje vytvořit typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.

2. Nastaví <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnotu v konstruktoru s [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] datové šablony. To je možné vytvořit v XAML, ale v této ukázce, tím se vytvoří v kódu.

3. Šablony má kontext dat objektu <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> vykreslen v mřížce vlastností položky. V následujícím kódu, poté vytvoří vazbu `Value` vlastnost. Je důležité zahrnout také <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> poskytnout tlačítka, které vyvolá dialogové okno v FilePickerEditor.cs.

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

4. Přepsání <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> metoda v typu návrháře pro zpracování zobrazení dialogového okna. V této ukázce základní <xref:System.Windows.Forms.FileDialog> se zobrazí.

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

5. Protože aktivity a návrháři jsou ve stejném sestavení, můžete registraci atributy návrháře aktivit provést v statický konstruktor aktivity, jak je znázorněno v následujícím příkladu od SimpleCodeActivity.cs.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Sestavte řešení a pak otevřete Workflow1.xaml.

2. Přetáhněte **SimpleCodeActivity** z panelu nástrojů do plátna návrháře.

3. Klikněte na tlačítko **SimpleCodeActivity** a pak otevřete mřížky vlastností níž se nachází na ovládacím prvku posuvník a soubor výběru ovládacího prvku.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
