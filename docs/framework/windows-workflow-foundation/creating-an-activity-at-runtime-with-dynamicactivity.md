---
title: Vytvoření aktivity za běhu pomocí dynamické aktivity
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: ed133e972caa9a3a62ab2ac1310cb1bd666947ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321224"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Vytvoření aktivity za běhu pomocí dynamické aktivity
<xref:System.Activities.DynamicActivity> je konkrétní zapečetěná třída s veřejným konstruktorem. <xref:System.Activities.DynamicActivity> je možné sestavit funkce aktivity za běhu pomocí aktivity modelu DOM.  
  
## <a name="dynamicactivity-features"></a>Funkce dynamické aktivity  
 <xref:System.Activities.DynamicActivity> má přístup k vlastnostem provádění, argumentů a proměnné, ale žádný přístup ke službám za běhu, jako je plánování podřízené aktivity nebo sledování.  
  
 Vlastnosti nejvyšší úrovně můžete nastavit pomocí pracovního postupu <xref:System.Activities.Argument> objekty. Tyto argumenty v imperativního kódu jsou vytvořeny pomocí vlastnosti CLR na nový typ. V XAML, jsou deklarovány pomocí `x:Class` a `x:Member` značky.  
  
 Aktivity, které jsou vytvářeny pomocí <xref:System.Activities.DynamicActivity> rozhraní s použitím návrháře <xref:System.ComponentModel.ICustomTypeDescriptor>. Aktivity vytvořené v Návrháři můžete načíst dynamicky pomocí <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak je ukázáno v následujícím postupu.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Vytvoření aktivity za běhu pomocí imperativního kódu  
  
1. OpenVisual Studio 2010.  
  
2. Vyberte **souboru**, **nové**, **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu. Vyberte **Konzolová aplikace sekvenčního pracovního postupu** v **šablony** okna. Název nového projektu DynamicActivitySample.  
  
3. Klikněte pravým tlačítkem na Workflow1.xaml HelloActivity projektu a vyberte **odstranit**.  
  
4. Otevřete soubor Program.cs. Na začátek souboru přidejte následující direktivy.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5. Nahraďte obsah `Main` metodu s následujícím kódem, který vytvoří <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje jediný <xref:System.Activities.Statements.WriteLine> aktivity a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> vlastnost nové dynamické aktivity.  
  
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
  
6. Spuštění aplikace. Okno konzoly s textem "Hello World!" zobrazí.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Vytvoření aktivity za běhu pomocí XAML  
  
1. Open Visual Studio 2010.  
  
2. Vyberte **souboru**, **nové**, **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** okna a vyberte **v2010** uzlu. Vyberte **Konzolová aplikace pracovního postupu** v **šablony** okna. Název nového projektu DynamicActivitySample.  
  
3. Otevřete v projektu HelloActivity Workflow1.xaml. Klikněte na tlačítko **argumenty** možnost v dolní části návrháře. Vytvořte nový `In` argument volá `TextToWrite` typu `String`.  
  
4. Přetáhněte **WriteLine** aktivita z **primitiv** části panelu nástrojů na plochu návrháře. Přiřaďte hodnotu `TextToWrite` k **Text** vlastnost aktivity.  
  
5. Otevřete soubor Program.cs. Na začátek souboru přidejte následující direktivy.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6. Nahraďte obsah `Main` metodu s následujícím kódem.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. Spuštění aplikace. Okno konzoly s textem "Hello World!" Zobrazí se.  
  
8. Klikněte pravým tlačítkem na soubor Workflow1.xaml v **Průzkumníka řešení** a vyberte **zobrazit kód**. Všimněte si, že třídy activity se vytvoří s `x:Class` a vlastnost se vytvoří s `x:Property`.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md)
