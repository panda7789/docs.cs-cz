---
title: Vytvoření aktivity za běhu pomocí DynamicActivity
description: DynamicActivity je konkrétní zapečetěná třída s veřejným konstruktorem. Použijte třídu k sestavení funkcí aktivity za běhu pomocí modelu DOM aktivity.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421537"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Vytvoření aktivity za běhu pomocí DynamicActivity
<xref:System.Activities.DynamicActivity>je konkrétní zapečetěná třída s veřejným konstruktorem. <xref:System.Activities.DynamicActivity>dá se použít k sestavování funkčnosti aktivity za běhu pomocí modelu DOM aktivity.  
  
## <a name="dynamicactivity-features"></a>Funkce DynamicActivity  
 <xref:System.Activities.DynamicActivity>má přístup k vlastnostem spuštění, argumentům a proměnným, ale nemá přístup ke službám runtime, jako je plánování podřízených aktivit nebo sledování.  
  
 Vlastnosti nejvyšší úrovně lze nastavit pomocí objektů pracovního postupu <xref:System.Activities.Argument> . V imperativním kódu jsou tyto argumenty vytvořeny pomocí vlastností CLR pro nový typ. V jazyce XAML jsou deklarovány pomocí `x:Class` `x:Member` značek a.  
  
 Aktivity vytvořené pomocí <xref:System.Activities.DynamicActivity> rozhraní s návrhářem pomocí <xref:System.ComponentModel.ICustomTypeDescriptor> . Aktivity vytvořené v Návrháři lze dynamicky načíst pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> , jak je znázorněno v následujícím postupu.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Vytvoření aktivity za běhu pomocí imperativního kódu  
  
1. OpenVisual Studio 2010.  
  
2. Vyberte **soubor**, **Nový**, **projekt**. V okně **typy projektů** vyberte **pracovní postup 4,0** v jazyce **Visual C#** a vyberte uzel **v2010** . V okně **šablony** vyberte **Konzolová aplikace sekvenčního pracovního postupu** . Pojmenujte nový projekt DynamicActivitySample.  
  
3. Klikněte pravým tlačítkem na Workflow1. XAML v projektu HelloActivity a vyberte **Odstranit**.  
  
4. Otevřete Program.cs. Do horní části souboru přidejte následující direktivu.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. Nahraďte obsah `Main` metody následujícím kódem, který vytvoří <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje jednu <xref:System.Activities.Statements.WriteLine> aktivitu a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> Vlastnosti nové dynamické aktivity.  
  
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
  
6. Spusťte aplikaci. Okno konzoly s textem "Hello World!" uvádí.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Vytvoření aktivity za běhu pomocí XAML  
  
1. Otevřete Visual Studio 2010.  
  
2. Vyberte **soubor**, **Nový**, **projekt**. V okně **typy projektů** vyberte **pracovní postup 4,0** v jazyce **Visual C#** a vyberte uzel **v2010** . V okně **šablony** vyberte **Konzolová aplikace pracovního postupu** . Pojmenujte nový projekt DynamicActivitySample.  
  
3. Otevřete Workflow1. XAML v projektu HelloActivity. Klikněte na možnost **argumenty** v dolní části návrháře. Vytvořte nový `In` argument nazvaný `TextToWrite` typu `String` .  
  
4. Přetáhněte aktivitu **WriteLine** z oddílu **primitivních** prvků sady nástrojů na plochu návrháře. Přiřaďte hodnotu `TextToWrite` k vlastnosti **text** aktivity.  
  
5. Otevřete Program.cs. Do horní části souboru přidejte následující direktivu.  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Obsah metody `Main` nahraďte následujícím kódem.  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Spusťte aplikaci. Okno konzoly s textem "Hello World!" uvedeny.  
  
8. Klikněte pravým tlačítkem na soubor Workflow1. XAML v **Průzkumník řešení** a vyberte **Zobrazit kód**. Všimněte si, že třída Activity je vytvořena s `x:Class` a vlastnost je vytvořena pomocí `x:Property` .  
  
## <a name="see-also"></a>Viz také

- [Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md)
