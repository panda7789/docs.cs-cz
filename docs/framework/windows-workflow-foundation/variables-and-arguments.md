---
title: Proměnné a argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 29ce5222435b68ed13cbc967e58e72a937625e8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669482"
---
# <a name="variables-and-arguments"></a>Proměnné a argumenty
Ve Windows Workflow Foundation (WF), proměnné představují úložiště dat a argumenty představují tok dat do a z aktivity. Aktivita má sadu argumentů a tvoří podpis aktivity. Kromě toho aktivita můžete udržovat seznam proměnných, do kterých Vývojář můžete přidávat nebo odebírat proměnné při návrhu pracovního postupu. Argument je vázán vlastnosti autorefresh pomocí výrazu, který vrací hodnotu.  
  
## <a name="variables"></a>Proměnné  
 Proměnné jsou umístění úložiště pro data. Proměnné jsou deklarovány jako součást definice pracovního postupu. Využijte proměnné na hodnoty v době běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu. Definice proměnné určuje typ proměnné a volitelně také název. Následující kód ukazuje, jak deklarovat proměnné, přiřadit hodnotu pomocí <xref:System.Activities.Statements.Assign%601> aktivitu a zobrazte její hodnotu na pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.  
  
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
  
 Volitelně můžete zadat výraz výchozí hodnoty jako součást deklarace proměnné. Proměnné také můžete mít modifikátory. Pro příklad, pokud je proměnná jen pro čtení a jen pro čtení <xref:System.Activities.VariableModifiers> lze použít modifikátor. V následujícím příkladu se vytvoří proměnnou jen pro čtení, který má přiřazenu výchozí hodnotu.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Proměnná rozsahu  
 Životnost proměnné v době běhu je rovna hodnotě doba života aktivity, která jej deklaruje. Po dokončení aktivity své proměnné se vyčistí a můžete se už neodkazuje.  
  
## <a name="arguments"></a>Arguments  
 Autoři aktivity používat argumenty pro definování dat, způsob putuje do a z aktivity. Každý argument má směr zadaný: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, nebo <xref:System.Activities.ArgumentDirection.InOut>.  
  
 Modul workflow runtime zaručuje následující skutečnosti o časování přesun dat do a z aktivity:  
  
1. Při spuštění aktivity spuštění se počítají hodnoty všech argumentů vstupu a vstupu a výstupu. Například, bez ohledu na to při <xref:System.Activities.Argument.Get%2A> je volána, vrácená hodnota se počítá ten modulem runtime před jeho vyvolání `Execute`.  
  
2. Když <xref:System.Activities.InOutArgument%601.Set%2A> je volána, modul runtime nastaví hodnotu okamžitě.  
  
3. Argumenty můžou mít svoje <xref:System.Activities.Argument.EvaluationOrder%2A> zadané. <xref:System.Activities.Argument.EvaluationOrder%2A> je založený na nule hodnotu, která určuje pořadí, ve kterém je vyhodnocen argument. Ve výchozím nastavení, pořadí vyhodnocení argumentu není zadána a je rovna <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> hodnotu. Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> na hodnotu větší nebo rovna hodnotě nula. Chcete-li určit pořadí vyhodnocení pro tento argument. Windows Workflow Foundation vyhodnotí argumentů s pořadím vyhodnocení zadané ve vzestupném pořadí. Všimněte si, že před těmi, které mají zadanou evaluationorder jsou vyhodnoceny argumenty s objednávkou neurčené hodnocení.  
  
 Autor aktivity můžete použít mechanismus silného typu pro vystavení svých argumentů. Toho lze dosáhnout deklarování vlastností typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>. To umožňuje autorovi aktivity stanovit konkrétní smlouvy o data přicházející do proměnné a z aktivity.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definování argumenty pro aktivitu  
 Argumenty můžete definovat pro aktivitu tak, že zadáte vlastnosti typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>. Následující kód ukazuje, jak definovat argumenty `Prompt` aktivitu, která přijímá řetězec k zobrazení pro uživatele a vrátí řetězec, který obsahuje odpověď uživatele.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Aktivity, které vrátí jednu hodnotu lze odvodit z <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, nebo <xref:System.Activities.CodeActivity%601>. Tyto aktivity mají jasně definovaných <xref:System.Activities.OutArgument%601> s názvem <xref:System.Activities.Activity%601.Result%2A> , který obsahuje vrácenou hodnotu aktivity.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Použití proměnných a argumentů v pracovních postupech  
 Následující příklad ukazuje, jak proměnné a argumenty se používají v pracovním postupu. Pracovní postup je sekvence, která deklaruje tří proměnných: `var1`, `var2`, a `var3`. První aktivitu v pracovním postupu je `Assign` aktivity, který přiřazuje hodnotu proměnné `var1` proměnné `var2`. Následuje `WriteLine` aktivitu, která vytiskne hodnotu `var2` proměnné. Dále je další `Assign` aktivity, který přiřazuje hodnotu proměnné `var2` proměnné `var3`. Nakonec je jiný `WriteLine` aktivitu, která vytiskne hodnotu `var3` proměnné. První `Assign` používá aktivitu `InArgument<string>` a `OutArgument<string>` objekty, které explicitně představují vazby pro argumenty aktivity. `InArgument<string>` slouží k <xref:System.Activities.Statements.Assign.Value%2A> vzhledem k tomu, že hodnota se přenášejí do <xref:System.Activities.Statements.Assign%601> aktivity prostřednictvím jeho <xref:System.Activities.Statements.Assign.Value%2A> argument, a `OutArgument<string>` se používá pro <xref:System.Activities.Statements.Assign.To%2A> vzhledem k tomu, že hodnota se přenášejí z celkového počtu <xref:System.Activities.Statements.Assign.To%2A> argument do proměnné. Druhá `Assign` aktivity totéž provede další compact ale ekvivalentní syntax, který používá implicitní přetypování. `WriteLine` Aktivity také používají nejúspornější syntaxí.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Pomocí proměnné a argumenty aktivity založený na kódu  
 Předchozí příklady ukazují, jak používat argumenty a proměnných v pracovních postupech a deklarativní aktivity. Proměnné a argumenty se používají také v aktivity založený na kódu. Využití je obecně velmi podobné. Proměnné představují úložiště dat v rámci aktivity a argumenty představují tok dat do nebo z něj aktivity a jsou vázány, které představují, kde se data posílají do nebo z jiných proměnných nebo argumentů v pracovním postupu Autor pracovního postupu. Chcete-li get nebo set, použita hodnota proměnné nebo argumentu do aktivity, objekt context aktivita, která představuje aktuální prostředí provádění aktivity. To je předán <xref:System.Activities.CodeActivity%601.Execute%2A> metodu činnosti pomocí modulu runtime pracovního postupu. V tomto příkladu vlastní `Add` aktivity je definován, která má dvě <xref:System.Activities.ArgumentDirection.In> argumenty. Pro přístup k hodnotě argumenty, <xref:System.Activities.Argument.Get%2A> metoda se používá a je použit kontext, který byl předán pomocí modulu runtime pracovního postupu.  
  
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
  
 Další informace o práci s argumenty, proměnné a výrazy v kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [povinné argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).
