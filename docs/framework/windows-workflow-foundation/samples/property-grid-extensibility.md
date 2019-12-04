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
# <a name="property-grid-extensibility"></a>Rozšíření mřížky vlastností

Vývojář může přizpůsobit mřížku vlastností, která se zobrazí při výběru dané aktivity v návrháři. To se dá udělat, aby se vytvořilo prostředí s bohatou úpravou. Tato ukázka ukazuje, jak to lze provést.

## <a name="demonstrates"></a>Demonstruje

Rozšiřitelnost mřížky vlastností návrháře pracovního postupu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>Účely

Chcete-li rozšířit mřížku vlastností, vývojář obsahuje možnosti přizpůsobení vloženého vzhledu editoru mřížky vlastností nebo poskytnutí dialogového okna, které se zobrazí pro pokročilejší editační plochu. V této ukázce jsou znázorněny dva různé editory. vložený Editor a editor dialogových oken.

## <a name="inline-editor"></a>Vložený Editor

Ukázka vloženého editoru znázorňuje následující:

- Vytvoří typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.

- V konstruktoru je hodnota <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> nastavena pomocí šablony dat Windows Presentation Foundation (WPF). Tato možnost může být vázána na šablonu XAML, ale v této ukázce se pro inicializaci datové vazby používá kód.

- Datová šablona má kontext dat <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky vykreslené v mřížce vlastností. Všimněte si, že v následujícím kódu (z CustomInlineEditor.cs) se tento kontext váže k vlastnosti `Value`.

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

- Vzhledem k tomu, že aktivita a Návrhář jsou ve stejném sestavení, probíhá registrace atributů návrháře aktivit ve statickém konstruktoru samotné aktivity, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.

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

Ukázka v editoru dialogových oken ukazuje následující:

1. Vytvoří typ, který je odvozen z <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.

2. Nastaví hodnotu <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> v konstruktoru pomocí šablony dat WPF. To lze vytvořit v jazyce XAML, ale v této ukázce je vytvořena v kódu.

3. Datová šablona má kontext dat <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky vykreslené v mřížce vlastností. V následujícím kódu se pak vytvoří vazba na vlastnost `Value`. Je důležité také zahrnout <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> k poskytnutí tlačítka, které vyvolává dialog v FilePickerEditor.cs.

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

4. Přepíše metodu <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> v typu návrháře pro zpracování zobrazení dialogového okna. V této ukázce se zobrazuje základní <xref:System.Windows.Forms.FileDialog>.

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

5. Vzhledem k tomu, že aktivita a Návrhář jsou ve stejném sestavení, probíhá registrace atributů návrháře aktivit ve statickém konstruktoru samotné aktivity, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Sestavte řešení a pak otevřete Workflow1. XAML.

2. Přetáhněte **SimpleCodeActivity** z panelu nástrojů na plátno návrháře.

3. Klikněte na **SimpleCodeActivity** a pak otevřete mřížku vlastností, kde je ovládací prvek posuvníku a ovládací prvek pro výdej souboru.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
