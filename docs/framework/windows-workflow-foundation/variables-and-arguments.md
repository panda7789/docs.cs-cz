---
title: Proměnné a argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: f975f46a1858d204d12588f7570b7ea5a365e650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182684"
---
# <a name="variables-and-arguments"></a>Proměnné a argumenty
V základech pracovních postupů systému Windows (WF) představují proměnné ukládání dat a argumenty tok dat do a z aktivity. Aktivita má sadu argumentů a tvoří podpis aktivity. Kromě toho aktivita může udržovat seznam proměnných, ke kterým může vývojář přidávat nebo odebírat proměnné během návrhu pracovního postupu. Argument je vázán pomocí výrazu, který vrací hodnotu.  
  
## <a name="variables"></a>Proměnné  
 Proměnné jsou umístění úložiště pro data. Proměnné jsou deklarovány jako součást definice pracovního postupu. Proměnné přebírají hodnoty za běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu. Definice proměnné určuje typ proměnné a volitelně název. Následující kód ukazuje, jak deklarovat proměnnou, <xref:System.Activities.Statements.Assign%601> přiřadit hodnotu k ní pomocí <xref:System.Activities.Statements.WriteLine> aktivity a potom zobrazit jeho hodnotu konzoly pomocí aktivity.  
  
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
  
 Výraz výchozí hodnoty lze volitelně zadat jako součást deklarace proměnné. Proměnné mohou mít také modifikátory. Například pokud je proměnná jen pro čtení, pak lze použít modifikátor jen pro <xref:System.Activities.VariableModifiers> čtení. V následujícím příkladu je vytvořena proměnná jen pro čtení, která má přiřazenou výchozí hodnotu.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Posunutí proměnných  
 Životnost proměnné za běhu se rovná životnosti aktivity, která ji deklaruje. Po dokončení aktivity jsou její proměnné vyčištěny a již nelze na ně odkazovat.  
  
## <a name="arguments"></a>Argumenty  
 Autoři aktivity používají argumenty k definování způsobu toku dat do a z aktivity. Každý argument má zadaný směr: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, nebo <xref:System.Activities.ArgumentDirection.InOut>.  
  
 Modul runtime pracovního postupu poskytuje následující záruky o načasování přesunu dat do a z aktivit:  
  
1. Když aktivita spustí, hodnoty všech jeho vstupní a vstupní/výstupní argumenty jsou vypočteny. Například bez ohledu <xref:System.Activities.Argument.Get%2A> na to, kdy je volána, je vrácená hodnota `Execute`hodnota vypočtená za běhu před jeho vyvoláním .  
  
2. Při <xref:System.Activities.InOutArgument%601.Set%2A> volání, runtime nastaví hodnotu okamžitě.  
  
3. Argumenty mohou mít <xref:System.Activities.Argument.EvaluationOrder%2A> volitelně zadaná. <xref:System.Activities.Argument.EvaluationOrder%2A>je hodnota založená na nule, která určuje pořadí, ve kterém je argument vyhodnocen. Ve výchozím nastavení pořadí vyhodnocení argumentu není určeno <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> a rovná se hodnotě. Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> hodnotu větší nebo rovnou nule pro určení pořadí hodnocení pro tento argument. Windows Workflow Foundation vyhodnocuje argumenty se zadaným pořadím hodnocení ve vzestupném pořadí. Všimněte si, že argumenty s nespecifikovanou pořadí hodnocení jsou vyhodnoceny před těmi, s zadané pořadí hodnocení.  
  
 Autor aktivity může použít mechanismus silného typu pro vystavení jeho argumenty. Toho lze dosáhnout deklarováním <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>vlastností <xref:System.Activities.InOutArgument%601>typu , a . To umožňuje autorovi aktivity vytvořit konkrétní smlouvu o datech, která přecvádějí do a z aktivity.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definování argumentů pro aktivitu  
 Argumenty lze definovat na aktivitu zadáním <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>vlastností <xref:System.Activities.InOutArgument%601>typu , a . Následující kód ukazuje, jak definovat argumenty pro aktivitu, `Prompt` která trvá v řetězci zobrazit uživateli a vrátí řetězec, který obsahuje odpověď uživatele.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Aktivity, které vracejí jednu hodnotu, mohou být odvozeny z , <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>, nebo <xref:System.Activities.CodeActivity%601>. Tyto aktivity mají <xref:System.Activities.OutArgument%601> dobře <xref:System.Activities.Activity%601.Result%2A> definovaný název, který obsahuje vrácenou hodnotu aktivity.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Použití proměnných a argumentů v pracovních postupech  
 Následující příklad ukazuje, jak se proměnné a argumenty používají v pracovním postupu. Pracovní postup je posloupnost, která `var1` `var2`deklaruje tři proměnné: , a `var3`. První aktivita v pracovním `Assign` postupu je aktivita, `var1` která `var2`přiřazuje hodnotu proměnné proměnné . Následuje aktivita, `WriteLine` která vytiskne `var2` hodnotu proměnné. Další je `Assign` další aktivita, která `var2` přiřazuje hodnotu proměnné proměnné `var3`. Nakonec je `WriteLine` další aktivita, která `var3` vytiskne hodnotu proměnné. První `Assign` aktivita `InArgument<string>` `OutArgument<string>` používá a objekty, které explicitně představují vazby pro argumenty aktivity. `InArgument<string>`se používá <xref:System.Activities.Statements.Assign.Value%2A> pro, protože hodnota <xref:System.Activities.Statements.Assign%601> proudí <xref:System.Activities.Statements.Assign.Value%2A> do `OutArgument<string>` aktivity <xref:System.Activities.Statements.Assign.To%2A> prostřednictvím jeho argument a <xref:System.Activities.Statements.Assign.To%2A> slouží pro, protože hodnota je toku z argumentu do proměnné. Druhá `Assign` aktivita provádí stejnou věc s kompaktnější, ale ekvivalentní syntaxe, která používá implicitní přetypován. Aktivity `WriteLine` také použít kompaktní syntaxi.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Použití proměnných a argumentů v aktivitách založených na kódu  
 Předchozí příklady ukazují, jak používat argumenty a proměnné v pracovních postupech a deklarativních aktivitách. Argumenty a proměnné se také používají v aktivitách založených na kódu. Koncepčně použití je velmi podobné. Proměnné představují ukládání dat v rámci aktivity a argumenty představují tok dat do nebo z aktivity a jsou vázány autorem pracovního postupu na jiné proměnné nebo argumenty v pracovním postupu, které představují, kde data toky do nebo z. Chcete-li získat nebo nastavit hodnotu proměnné nebo argumentu v aktivitě, musí být použit kontext aktivity, který představuje aktuální prostředí provádění aktivity. To je předáno <xref:System.Activities.CodeActivity%601.Execute%2A> do metody aktivity za běhu pracovního postupu. V tomto příkladu `Add` je definována <xref:System.Activities.ArgumentDirection.In> vlastní aktivita, která má dva argumenty. Pro přístup k hodnotě argumentů se používá <xref:System.Activities.Argument.Get%2A> metoda a kontext, který byl předán v běhu pracovního postupu.  
  
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
  
 Další informace o práci s argumenty, proměnnými a výrazy v kódu naleznete v [tématu Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [požadovaných argumentů a skupin přetížení](required-arguments-and-overload-groups.md).
