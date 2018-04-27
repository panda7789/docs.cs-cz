---
title: Proměnné a argumenty
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c81d05120f8cf0decc7c6036e2a722ba6271dab8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="variables-and-arguments"></a>Proměnné a argumenty
V systému Windows Workflow Foundation (WF), proměnné představují úložiště dat a argumenty představují tok dat do a z aktivity. Aktivita má sadu argumentů a jejich tvoří podpis aktivity. Kromě toho aktivitu můžete spravovat seznam proměnné, do kterých vývojář lze přidávat nebo odebírat proměnné při návrhu pracovního postupu. Argument je svázán pomocí výraz, který vrátí hodnotu.  
  
## <a name="variables"></a>Proměnné  
 Proměnné jsou umístění úložiště pro data. Proměnné jsou deklarovány jako součást definice pracovního postupu. Proměnné trvat na hodnoty v době běhu a tyto hodnoty se uloží jako součást stavu instance pracovního postupu. Definice proměnných Určuje typ proměnné a volitelně název. Následující kód ukazuje, jak deklarace proměnné, přiřadit hodnotu se pomocí <xref:System.Activities.Statements.Assign%601> aktivity a následně na pomocí konzoly se zobrazí jeho hodnotu <xref:System.Activities.Statements.WriteLine> aktivity.  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Výraz výchozí hodnoty Volitelně můžete zadat jako součást deklarace proměnné. Proměnné můžete mít také modifikátory. Pro příklad, pokud je proměnná jen pro čtení a jen pro čtení <xref:System.Activities.VariableModifiers> modifikátor lze použít. V následujícím příkladu se vytvoří proměnnou jen pro čtení, který má přiřazenu hodnotu výchozí.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Proměnné rozsahu  
 Doba života proměnné v době běhu nastavena na dobu životnosti aktivity, který deklaruje ho. Po dokončení aktivity jeho proměnné jsou vyčištění a může se už neodkazuje.  
  
## <a name="arguments"></a>Arguments  
 Autoři aktivity argumenty použít k definování dat způsob toků do a z aktivity. Každý argument má zadaný směr: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, nebo <xref:System.Activities.ArgumentDirection.InOut>.  
  
 Modul runtime pracovního postupu provede následující záruky o načasování přesun dat do a z aktivity:  
  
1.  Při spuštění provádění aktivity jsou vypočítávány hodnoty všechny argumenty vstupní a vstupu a výstupu. Například, bez ohledu na to při <xref:System.Activities.Argument.Get%2A> je volána, vrácená hodnota je vypočítána ten modulem runtime před jeho vyvolání `Execute`.  
  
2.  Když <xref:System.Activities.InOutArgument%601.Set%2A> je volána, modul runtime nastaví hodnotu okamžitě.  
  
3.  Argumenty můžete volitelně může mít jejich <xref:System.Activities.Argument.EvaluationOrder%2A> zadaný. <xref:System.Activities.Argument.EvaluationOrder%2A> je počítáno od nuly hodnotu, která určuje pořadí, ve kterém je vyhodnocena argument. Ve výchozím nastavení, pořadí vyhodnocení argumentu neurčené a rovná <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> hodnotu. Nastavit <xref:System.Activities.Argument.EvaluationOrder%2A> na hodnotu větší nebo rovna hodnotě nula. k určení pořadí vyhodnocení pro tento argument. Windows Workflow Foundation vyhodnotí argumenty s pořadí zadaný vyhodnocení ve vzestupném pořadí. Všimněte si, že argumenty k vyhodnocení neurčené pořadí se vyhodnocují před akcemi s pořadí zadaný vyhodnocení.  
  
 Autor aktivitu můžete použít silného typu mechanismus pro vystavení její argumenty. To lze provést deklarace vlastnosti typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>. To umožňuje autorovi aktivity k vytvoření kontraktu konkrétní týkající se dat do a z aktivity.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definování argumenty u aktivit  
 Argumenty můžete definovat na aktivitu zadáním vlastnosti typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>. Následující kód ukazuje, jak definovat argumentů `Prompt` aktivity, která přebírá řetězec k zobrazení pro uživatele a vrátí řetězec, který obsahuje odpověď uživatele.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Aktivity, které vrátí jednu hodnotu můžete odvozeny od <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, nebo <xref:System.Activities.CodeActivity%601>. Tyto aktivity mít dobře definované <xref:System.Activities.OutArgument%601> s názvem <xref:System.Activities.Activity%601.Result%2A> obsahující návratovou hodnotu aktivity.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Použití proměnných a argumenty v pracovních postupech  
 Následující příklad ukazuje, jak používat proměnné a argumenty v pracovním postupu. Pracovní postup je pořadí, který deklaruje tří proměnných: `var1`, `var2`, a `var3`. Je první aktivitu v pracovním postupu `Assign` aktivity, který přiřazuje hodnotu proměnné `var1` proměnnou `var2`. Následují `WriteLine` aktivity, která se vytiskne hodnota `var2` proměnné. Následuje jiný `Assign` aktivity, který přiřazuje hodnotu proměnné `var2` proměnnou `var3`. Nakonec je jiné `WriteLine` aktivity, která se vytiskne hodnota `var3` proměnné. První `Assign` aktivita používá `InArgument<string>` a `OutArgument<string>` objekty, které explicitně představují vazby u aktivity argumenty. `InArgument<string>` slouží k <xref:System.Activities.Statements.Assign.Value%2A> vzhledem k tomu, že hodnota je odesílaných do <xref:System.Activities.Statements.Assign%601> aktivity prostřednictvím jeho <xref:System.Activities.Statements.Assign.Value%2A> argument, a `OutArgument<string>` se používá pro <xref:System.Activities.Statements.Assign.To%2A> vzhledem k tomu, že hodnota je předávaných mimo <xref:System.Activities.Statements.Assign.To%2A> argument do proměnné. Druhý `Assign` aktivita provede stejnou věc s více compact ale ekvivalentní syntaxi, která používá implicitní přetypování. `WriteLine` Aktivity také syntaxí compact.  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Použití proměnných a argumenty v aktivitách, založené na kódu  
 Předchozí příklady ukazují, jak používat argumentů a proměnných v pracovních postupů a deklarativní aktivit. Argumenty a proměnné se také používají v aktivitách, založené na kódu. Využití je koncepčně velmi podobné. Proměnné představují úložiště dat v rámci aktivity a argumenty představují tok dat do nebo z aktivity a jsou vázány představující kde tok dat do nebo z na jiné proměnné nebo argumenty v pracovním postupu Autor pracovního postupu. Get nebo sadu musí použít hodnotu proměnné nebo argumentu v aktivitě, kontextu aktivity, který představuje aktuální prostředí pro spuštění aktivity. To je předána do <xref:System.Activities.CodeActivity%601.Execute%2A> metoda aktivity modulem runtime pracovního postupu. V tomto příkladu vlastní `Add` je definována aktivity, která má dva <xref:System.Activities.ArgumentDirection.In> argumenty. Pro přístup k hodnotě argumenty, <xref:System.Activities.Argument.Get%2A> metoda se používá a kontext, který byl předán v modulem runtime pracovního postupu.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] Práce s argumenty, proměnné a výrazy v kódu, najdete v části [vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) a [vyžaduje argumenty a přetížení skupiny](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).
