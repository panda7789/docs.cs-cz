---
title: "Vlastnosti pracovního postupu provádění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d119d721964df7ea1c007eadd17a8db54f4f8cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-execution-properties"></a>Vlastnosti pracovního postupu provádění
Pomocí místní úložiště vláken (TLS) modul CLR udržuje kontextu spuštění pro každé vlákno. Tento kontext spuštění řídí vlastnosti dobře známé vlákna například identity vláken vedlejším transakce a sadou kromě vlákno uživatelem definované vlastnosti jako aktuální oprávnění s názvem sloty.  
  
 Na rozdíl od přímo cílení na modulu CLR programů jsou programy pracovního postupu hierarchicky vymezená stromy aktivit, které se spouští v prostředí bez ohledu na vlákno. To znamená, že standardních mechanismů TLS nelze použít přímo k určení, jaké kontext je v oboru pro daný pracovní položku. Například dvě paralelních větvích provádění může používat jinou transakcí, ale Plánovač může interleave jejich spuštění ve stejném vlákně, CLR.  
  
 Pracovní postup provádění vlastnosti poskytují mechanismus k přidání konkrétních vlastností kontextu do prostředí aktivity. To umožňuje aktivitu deklarovat, vlastnosti, které jsou v oboru pro jeho podstromu a také poskytuje háky pro nastavení a zrušení TLS správně vzájemnou spolupráci s objekty CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Vytvoření a použití vlastností pracovního postupu provádění  
 Pracovní postup provádění vlastnosti obvykle implementovat <xref:System.Activities.IExecutionProperty> rozhraní, i když vlastnosti, které jsou zaměřené na zasílání zpráv může implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo. Pokud chcete vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementovat členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Tito členové poskytnout vlastnost provádění příležitost správně nastavit a přerušit lokální úložiště vláken při každé pulse pracovní aktivity, která obsahuje vlastnosti, včetně žádné podřízené aktivity. V tomto příkladu `ConsoleColorProperty` této sady je vytvořena `Console.ForegroundColor`.  
  
> [!NOTE]
>  Následující příklad kódu v tomto tématu podle [provádění vlastnosti](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) ukázka.  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 Autoři aktivitu můžete použít tuto vlastnost tak, že zaregistrujete v aktivity spustit přepsání. V tomto příkladu `ConsoleColorScope` aktivity je definován, se zaregistruje `ConsoleColorProperty` přidáním jeho <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuální <xref:System.Activities.NativeActivityContext>.  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 Při spuštění aktivity textu pulse práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> je volána metoda vlastnosti a po dokončení, pulse práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> je volána. V tomto příkladu se vytvoří pracovní postup používající <xref:System.Activities.Statements.Parallel> aktivitu tři větve. Použít první dvě pobočky `ConsoleColorScope` aktivity a třetí větev neexistuje. Všechny tři větve obsahovat dvě <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Delay> aktivity. Když <xref:System.Activities.Statements.Parallel> provádí aktivity, aktivity, které jsou obsaženy v větve provést prokládaná způsobem, ale jako provádí každou aktivitu podřízené barvu konzoly správné použití je `ConsoleColorProperty`.  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =   
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =   
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Po vyvolání pracovní postup je následující výstup zapsán do okna konzoly.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  I když ho není zobrazené ve výstupu předchozí, každý řádek textu v okně konzoly se zobrazí v barvu uvedené.  
  
 Vlastnosti pracovního postupu provádění lze použít autory vlastní aktivitu, a také poskytují mechanismus pro Správa popisovačů pro aktivity, jako <xref:System.ServiceModel.Activities.CorrelationScope> a <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
