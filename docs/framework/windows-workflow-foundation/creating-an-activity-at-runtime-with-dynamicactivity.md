---
title: "Vytvoření aktivity za běhu s DynamicActivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d40fe3601cb8ad7c4f77cf50825da1deace5644e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a>Vytvoření aktivity za běhu s DynamicActivity
<xref:System.Activities.DynamicActivity>je třída konkrétní, zapečetěné s veřejný konstruktor. <xref:System.Activities.DynamicActivity>slouží ke kompilaci aktivita funkce za běhu pomocí aktivity modelu DOM.  
  
## <a name="dynamicactivity-features"></a>Funkce DynamicActivity  
 <xref:System.Activities.DynamicActivity>má přístup k vlastnosti provádění, argumentů a proměnné, ale žádný přístup k spuštění služby, jako je například plánování podřízené aktivity nebo sledování.  
  
 Nejvyšší úrovně vlastnosti se dá nastavit pomocí pracovního postupu <xref:System.Activities.Argument> objekty. Imperativní kódu se tyto argumenty vytvoří pomocí vlastnosti CLR na nový typ. V jazyce XAML, jsou deklarovány pomocí `x:Class` a `x:Member` značky.  
  
 Aktivity, které jsou vytvářeny pomocí <xref:System.Activities.DynamicActivity> rozhraní s použitím návrháře <xref:System.ComponentModel.ICustomTypeDescriptor>. Aktivity vytvořené v Návrháři můžete načíst pomocí dynamicky <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, jak je znázorněno v následujícím postupu.  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a>Chcete-li vytvořit aktivitu v době běhu pomocí imperativní kódu  
  
1.  Otevřete[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Vyberte **soubor**, **nové**, **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu. Vyberte **sekvenčního pracovního postupu konzolové aplikace** v **šablony** okno. Název nového projektu DynamicActivitySample.  
  
3.  Klikněte pravým tlačítkem na Workflow1.xaml v HelloActivity projektu a vyberte **odstranit**.  
  
4.  Otevření souboru Program.cs. Na začátek souboru přidejte následující direktivy.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
5.  Nahraďte obsah `Main` metoda následující kód, který vytvoří <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje jeden <xref:System.Activities.Statements.WriteLine> aktivity a přiřadí ji k <xref:System.Activities.DynamicActivity.Implementation%2A> vlastnost nové dynamické aktivity.  
  
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
  
6.  Spuštění aplikace. Okno konzoly s textem "Hello, World!" zobrazí.  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a>Chcete-li vytvořit aktivitu v době běhu pomocí jazyka XAML  
  
1.  Otevřete [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Vyberte **soubor**, **nové**, **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu. Vyberte **pracovního postupu konzolové aplikace** v **šablony** okno. Název nového projektu DynamicActivitySample.  
  
3.  Otevřete v projektu HelloActivity Workflow1.xaml. Klikněte **argumenty** možnost v dolní části návrháře. Vytvořte novou `In` argument názvem `TextToWrite` typu `String`.  
  
4.  Přetáhněte **WriteLine** aktivity z **primitiv** části panelu nástrojů na plochu návrháře. Přiřadí hodnotu `TextToWrite` k **Text** vlastnost aktivity.  
  
5.  Otevření souboru Program.cs. Na začátek souboru přidejte následující direktivy.  
  
    ```  
    using System.Activities.XamlIntegration;  
    ```  
  
6.  Nahraďte obsah `Main` metoda následujícím kódem.  
  
    ```  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7.  Spuštění aplikace. Okno konzoly s textem "Hello, World!" Zobrazí se.  
  
8.  Klikněte pravým tlačítkem na soubor Workflow1.xaml v **Průzkumníku řešení** a vyberte **kód zobrazení**. Všimněte si, že třídy aktivity je vytvořena s `x:Class` a vlastnost je vytvořena s `x:Property`.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)  
 [Vytvoření DynamicActivity](../../../docs/framework/windows-workflow-foundation/samples/dynamicactivity-creation.md)
