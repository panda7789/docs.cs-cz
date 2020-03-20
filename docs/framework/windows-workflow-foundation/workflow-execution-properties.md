---
title: Vlastnosti spuštění pracovního postupu
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182667"
---
# <a name="workflow-execution-properties"></a>Vlastnosti spuštění pracovního postupu
Prostřednictvím místního úložiště vlákna (TLS) clr udržuje kontext spuštění pro každé vlákno. Tento kontext spuštění řídí známé vlastnosti vlákna, jako je například identita vlákna, transakce okolí a aktuální sada oprávnění kromě uživatelem definovaných vlastností vlákna, jako jsou pojmenované sloty.  
  
 Na rozdíl od programů, které přímo cílí na CLR, jsou programy pracovního postupu hierarchicky vymezené stromy aktivit, které se provádějí v prostředí bez ohledu na vlákno. To znamená, že standardní tls mechanismy nelze přímo použít k určení, jaký kontext je v oboru pro danou pracovní položku. Například dvě paralelní větve provádění může používat různé transakce, ale plánovač může proložit jejich provádění ve stejném vlákně CLR.  
  
 Vlastnosti spuštění pracovního postupu poskytují mechanismus pro přidání vlastností specifických pro kontext do prostředí aktivity. To umožňuje aktivitu deklarovat, které vlastnosti jsou v oboru pro jeho podstrom a také poskytuje háčky pro nastavení a stržení TLS správně spolupracovat s objekty CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Vytváření a používání vlastností spuštění pracovního postupu  
 Vlastnosti spuštění pracovního postupu obvykle implementují <xref:System.Activities.IExecutionProperty> rozhraní, i když vlastnosti zaměřené na zasílání zpráv mohou implementovat <xref:System.ServiceModel.Activities.ISendMessageCallback> a <xref:System.ServiceModel.Activities.IReceiveMessageCallback> místo toho. Chcete-li vytvořit vlastnost spuštění pracovního postupu, vytvořte třídu, která implementuje <xref:System.Activities.IExecutionProperty> rozhraní a implementuje členy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> a <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Tyto členy poskytují spuštění vlastnost s možností správně nastavit a strhnout místní úložiště podprocesu během každého impulsu práce aktivity, která obsahuje vlastnost, včetně všech podřízených aktivit. V tomto příkladu je vytvořen a, `ConsoleColorProperty` který nastaví `Console.ForegroundColor`.  
  
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
  
 Autoři aktivity můžete použít tuto vlastnost registrací v přepsání spuštění aktivity. V tomto příkladu je `ConsoleColorScope` definována `ConsoleColorProperty` aktivita, která <xref:System.Activities.NativeActivityContext.Properties%2A> registruje <xref:System.Activities.NativeActivityContext>přidáním do kolekce aktuální .  
  
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
  
 Když tělo aktivity spustí puls práce, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> volá se metoda vlastnosti a po dokončení pulzu práce <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> se nazývá. V tomto příkladu je vytvořen <xref:System.Activities.Statements.Parallel> pracovní postup, který používá aktivitu se třemi větvemi. První dvě větve používají `ConsoleColorScope` aktivitu a třetí větev nepoužívá. Všechny tři větve <xref:System.Activities.Statements.WriteLine> obsahují dvě <xref:System.Activities.Statements.Delay> aktivity a aktivitu. Při <xref:System.Activities.Statements.Parallel> provádění aktivity aktivity, které jsou obsaženy v větvích provést proloženým způsobem, ale jako každá `ConsoleColorProperty`podřízená aktivita provede správnou barvu konzoly je použita .  
  
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
  
 Při vyvolání pracovního postupu je do okna konzoly zapsán následující výstup.  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Přestože není zobrazen v předchozím výstupu, každý řádek textu v okně konzoly se zobrazí v uvedené barvě.  
  
 Vlastnosti spuštění pracovního postupu mohou používat vlastní autoři aktivit a poskytují také <xref:System.ServiceModel.Activities.CorrelationScope> <xref:System.Activities.Statements.TransactionScope> mechanismus pro správu popisovače pro aktivity, jako jsou aktivity a.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
