---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f87e58a034cbc11565fc74347e6b4362952093c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974003"
---
# <a name="workflow-execution-properties"></a>Vlastnosti spuštění pracovního postupu
Pomocí úložiště thread local (TLS) CLR udržuje kontext spuštění pro každé vlákno. Tento kontext spuštění se řídí vlákno dobře známé vlastnosti, jako je identitu vlákna okolí transakce a sadou kromě vlákna uživatelem definované vlastnosti, jako je aktuální oprávnění s názvem sloty.  
  
 Na rozdíl od programy přímo cílí na modulu CLR pracovní postup programy jsou hierarchicky vymezené stromů aktivit, které jsou spuštěny v prostředí bez ohledu na vlákno. Z toho vyplývá, že standardních mechanismů protokolu TLS nelze přímo použít k určení, jaké kontext je v oboru pro daný pracovní položky. Například dva paralelních větvích provádění použít jiné transakce, ale Plánovač může prokládání jejich spuštění ve stejném vlákně modulu CLR.  
  
 Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání kontextu specifické vlastnosti aktivity prostředí. To umožňuje aktivitu, chcete-li deklarovat vlastnosti, které jsou v oboru pro jeho podstromu a také poskytuje zachytávání pro nastavení a opětné TLS správně zajistit vzájemnou funkční spolupráci s objekty CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Vytváření a používání běhové vlastnosti pracovního postupu  
 Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, když vlastnosti, zaměřuje na zasílání zpráv může implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo. Pro vytvoření vlastnosti spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementovat členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Tyto členy, poskytne vlastnost spuštění příležitost správně nastavit a začít odstraňovat úložiště thread local během každé pulse pracovní aktivity, která obsahuje vlastnosti, včetně všechny podřízené aktivity. V tomto příkladu `ConsoleColorProperty` vytvoření této sady `Console.ForegroundColor`.  
  
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
  
 Aktivita autoři tuto vlastnost můžete použít tak, že zaregistrujete ho v aktivity spuštění přepsat. V tomto příkladu `ConsoleColorScope` aktivity je definován, která se registruje `ConsoleColorProperty` tak, že ji přidáte <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuálního <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Při spuštění aktivity tělo pulse práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> volání metody, vlastnosti a po dokončení, pulse práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> je volána. V tomto příkladu se vytvoří pracovní postup, který používá <xref:System.Activities.Statements.Parallel> aktivity tři větví. Používat nejdřív dvě větve `ConsoleColorScope` aktivity a třetí větve tak není. Všechny tři větve obsahují dva <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Delay> aktivity. Když <xref:System.Activities.Statements.Parallel> aktivity spustí, aktivity, které jsou obsaženy v větve provést prokládané způsobem, ale protože každá podřízená aktivita spustí barvu správné konzole použití `ConsoleColorProperty`.  
  
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
  
 Když uživatel vyvolá pracovní postup, následující výstup je zapsán do okna konzoly.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  I když není zobrazený ve výstupu předchozí, jednotlivé řádky textu v okně konzoly se zobrazí v označeném barvu.  
  
 Vlastnosti spuštění pracovního postupu je možné autory vlastní aktivitu, a také poskytují mechanismus pro Správa popisovačů pro aktivity, jako <xref:System.ServiceModel.Activities.CorrelationScope> a <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
