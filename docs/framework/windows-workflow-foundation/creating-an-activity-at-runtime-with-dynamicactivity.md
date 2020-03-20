---
title: Vytvoření aktivity za běhu pomocí dynamické aktivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 871108fd09e9127b3f9e06174f05a47c7fd7682c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182983"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Vytvoření aktivity za běhu pomocí dynamické aktivity
<xref:System.Activities.DynamicActivity>je betonová, zapečetěná třída s veřejným konstruktérem. <xref:System.Activities.DynamicActivity>lze použít k sestavení funkce aktivity za běhu pomocí aktivity DOM.  
  
## <a name="dynamicactivity-features"></a>Funkce dynamice aktivity  
 <xref:System.Activities.DynamicActivity>má přístup k vlastnostem spuštění, argumentům a proměnným, ale nemá přístup ke službám za běhu, jako je plánování podřízených aktivit nebo sledování.  
  
 Vlastnosti nejvyšší úrovně lze <xref:System.Activities.Argument> nastavit pomocí objektů pracovního postupu. V imperativním kódu jsou tyto argumenty vytvořeny pomocí vlastností CLR u nového typu. V XAML jsou deklarovány pomocí `x:Class` a `x:Member` značky.  
  
 Aktivity vytvořené <xref:System.Activities.DynamicActivity> pomocí rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor>s návrhářem pomocí . Aktivity vytvořené v návrháři lze <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>načíst dynamicky pomocí , jak je znázorněno v následujícím postupu.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Vytvoření aktivity za běhu pomocí imperativního kódu  
  
1. OpenVisual Studio 2010.  
  
2. Vyberte **soubor**, **Nový**, **Projekt**. Vyberte **pracovní postup 4.0** v části **Visual C#** v okně **Typy projektů** a vyberte uzel **v2010.** V okně Šablony vyberte **Sekvenční konzolová aplikace** **pracovního postupu.** Pojmenujte nový projekt DynamicActivitySample.  
  
3. Klepněte pravým tlačítkem myši na soubor Workflow1.xaml v projektu HelloActivity a vyberte **příkaz Odstranit**.  
  
4. Otevřete Program.cs. Přidejte následující direktivu do horní části souboru.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Nahraďte obsah `Main` metody následujícím kódem, <xref:System.Activities.Statements.Sequence> který vytvoří aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.DynamicActivity.Implementation%2A> jednu aktivitu, a přiřadí ji vlastnosti nové dynamické aktivity.  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. Spusťte aplikaci. Okno konzoly s textem "Hello World!" Zobrazí.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Vytvoření aktivity za běhu pomocí xaml  
  
1. Otevřete Visual Studio 2010.  
  
2. Vyberte **soubor**, **Nový**, **Projekt**. Vyberte **pracovní postup 4.0** v části **Visual C#** v okně **Typy projektů** a vyberte uzel **v2010.** V okně **Šablony** vyberte **Konzolová aplikace pracovního postupu.** Pojmenujte nový projekt DynamicActivitySample.  
  
3. Otevřete soubor Workflow1.xaml v projektu HelloActivity. Klikněte na možnost **Argumenty** v dolní části návrháře. Vytvořte `In` nový `TextToWrite` argument `String`nazvaný typu .  
  
4. Přetáhněte aktivitu **WriteLine** z části **Primitiv** v panelu nástrojů na povrch návrháře. Přiřaďte hodnotu `TextToWrite` vlastnosti **Text** aktivity.  
  
5. Otevřete Program.cs. Přidejte následující direktivu do horní části souboru.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Obsah metody `Main` nahraďte následujícím kódem.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Spusťte aplikaci. Okno konzoly s textem "Hello World!" Zobrazí.  
  
8. Klepněte pravým tlačítkem myši na soubor Workflow1.xaml v **Průzkumníku řešení** a vyberte **příkaz Zobrazit kód**. Všimněte si, že `x:Class` třída aktivity je `x:Property`vytvořena s a vlastnost je vytvořena pomocí .  
  
## <a name="see-also"></a>Viz také

- [Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md)
