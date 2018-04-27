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
ms.openlocfilehash: 9393947420709590312200e8f142092c95b91b1f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="property-grid-extensibliity"></a>Vlastnost Extensibliity mřížky
Vývojář může přizpůsobit mřížku vlastností, které se zobrazí, pokud je vybrána danou aktivitu v návrháři. To lze provést pro vytvoření bohaté úpravy prostředí. Tento příklad ukazuje, jak to lze provést.  
  
## <a name="demonstrates"></a>Demonstruje  
 Rozšíření mřížky vlastnosti Návrháře pracovního postupu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a>Diskusní  
 Pokud chcete rozšířit mřížku vlastností, má vývojář možností pro přizpůsobení vzhledu vložené do editoru mřížky vlastnosti, nebo poskytněte dialog, který se zobrazí pro pokročilejší prostor pro úpravy. Existují dva různé editory předvedená v této ukázce; vložené editoru a editor dialogového okna.  
  
## <a name="inline-editor"></a>Vložené editoru  
 Ukázka editor vložené ukazuje následující:  
  
-   Vytvoří typ, který je odvozen od <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.  
  
-   V konstruktoru <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnota je nastavena pomocí šablony data Windows Presentation Foundation (WPF). To může být vázaný na šablonu XAML, ale v této ukázce kódu slouží k inicializaci datové vazby.  
  
-   Šablona dat má kontext dat z <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky v tabulce vlastností. Poznámka: v následujícím kódu (z CustomInlineEditor.cs), která tento kontext pak sváže `Value` vlastnost.  
  
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
  
-   Protože jsou ve stejném sestavení aktivity a návrháře, registrace atributů Návrhář aktivity lze provádět statického konstruktoru aktivity samostatně, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a>Editor dialogových oken  
 Dialogové okno editor ukázku ukazuje následující:  
  
1.  Vytvoří typ, který je odvozen od <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.  
  
2.  Nastaví <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> hodnotu v konstruktoru s [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] datová šablona. To lze vytvořit v jazyce XAML, ale v této ukázce je vytvořena v kódu.  
  
3.  Šablona dat má kontext dat z <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> položky v tabulce vlastností. V následujícím kódu, to pak váže `Value` vlastnost. Je důležité zahrnout také <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> zajistit tlačítko vyvolá dialogové okno ve FilePickerEditor.cs.  
  
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
  
4.  Přepsání <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` metoda v návrháře typu pro zpracování zobrazení dialogového okna. V této ukázce základní <xref:System.Windows.Forms.FileDialog> se zobrazí.  
  
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
  
5.  Protože jsou ve stejném sestavení aktivity a návrháře, registrace atributů Návrhář aktivity lze provádět statického konstruktoru aktivity samostatně, jak je znázorněno v následujícím příkladu z SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení a pak otevřete Workflow1.xaml.  
  
2.  Přetáhněte **SimpleCodeActivity** z panelu nástrojů do plátna návrháře.  
  
3.  Klikněte **SimpleCodeActivity** a pak otevřete mřížku vlastností, kde je ovládací prvek typu jezdec a soubor výběr ovládacího prvku.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
