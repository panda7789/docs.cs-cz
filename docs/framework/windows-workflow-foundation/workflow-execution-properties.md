---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 61bf53d9cab3ddefae3709958bd1e445fb4e69dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913612"
---
# <a name="workflow-execution-properties"></a>Vlastnosti spuštění pracovního postupu
Pomocí protokolu thread local Storage (TLS) udržuje modul CLR kontext spuštění pro každé vlákno. Tento kontext spuštění řídí dobře známé vlastnosti vlákna, jako je například identita vlákna, ambientní transakce a současná sada oprávnění kromě uživatelsky definovaných vlastností vlákna, jako jsou pojmenované sloty.  
  
 Na rozdíl od programů přímo cílících na CLR jsou programy pracovních postupů hierarchicky vymezené stromy aktivit, které se spouštějí v prostředí s nezávislá vláknem. To znamená, že standardní mechanismy TLS nelze přímo použít k určení kontextu, který je v rozsahu pro danou pracovní položku. Například dvě paralelní větve provádění mohou používat různé transakce, přesto může Plánovač prokládat jejich spuštění ve stejném vlákně CLR.  
  
 Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání specifických vlastností kontextu do prostředí aktivity. To umožňuje aktivitě deklarovat, které vlastnosti jsou v oboru pro jeho podstromy, a také poskytuje zapojování pro nastavení a odtržení protokolu TLS pro správné spolupráci s objekty CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Vytváření a používání vlastností spuštění pracovního postupu  
 Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, ale vlastnosti zaměřené na zasílání zpráv mohou implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo toho. Chcete-li vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která <xref:System.Activities.IExecutionProperty> implementuje rozhraní a implementuje členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Tito členové poskytují vlastnost spuštění s příležitostí ke správnému nastavení a odtrhnout thread local úložiště během každé pulsace práce aktivity obsahující vlastnost, včetně všech podřízených aktivit. V tomto příkladu je vytvořena `ConsoleColorProperty` sada, která `Console.ForegroundColor`nastavuje.  
  
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
  
 Autoři aktivity mohou tuto vlastnost používat tak, že ji zaregistrují v přepsání Execute aktivity. V tomto příkladu `ConsoleColorScope` je definována aktivita, která `ConsoleColorProperty` registruje přidáním do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekce aktuálního <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Když tělo aktivity začne pracovat na Pulse, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> je volána metoda vlastnosti a když je Pulse práce dokončena <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> , je volána. V tomto příkladu se vytvoří pracovní postup, který používá <xref:System.Activities.Statements.Parallel> aktivitu se třemi větvemi. První dvě větve používají `ConsoleColorScope` aktivitu a třetí větev ne. Všechny tři větve obsahují dvě <xref:System.Activities.Statements.WriteLine> aktivity <xref:System.Activities.Statements.Delay> a aktivitu. Když se <xref:System.Activities.Statements.Parallel> aktivita spustí, aktivity, které jsou obsaženy v větvích, se spustí způsobem prokládaným způsobem, ale každá podřízená aktivita spustí správnou barvu `ConsoleColorProperty`konzoly, kterou používá.  
  
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
  
 Po vyvolání pracovního postupu se do okna konzoly zapíše následující výstup.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> I když není zobrazený v předchozím výstupu, zobrazí se v označené barvě každý řádek textu v okně konzoly.  
  
 Vlastnosti spuštění pracovního postupu můžou použít vlastní autoři aktivity a také poskytují mechanismus pro správu pro aktivity, jako jsou <xref:System.ServiceModel.Activities.CorrelationScope> aktivity a. <xref:System.Activities.Statements.TransactionScope>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
