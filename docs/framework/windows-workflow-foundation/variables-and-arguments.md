---
title: Proměnné a argumenty
description: Tento článek popisuje proměnné, které reprezentují úložiště dat a argumenty, které reprezentují tok dat do/z aktivity v modelu Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 47b8a7bddc8c3a9a8427bcb3e93760a63e5fa976
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421303"
---
# <a name="variables-and-arguments"></a>Proměnné a argumenty
V programovací model Windows Workflow Foundation (WF) proměnné reprezentují úložiště dat a argumenty představuje tok dat do a z aktivity. Aktivita má sadu argumentů a tvoří podpis aktivity. Kromě toho aktivita může udržovat seznam proměnných, ke kterým může vývojář přidávat nebo odebírat proměnné během návrhu pracovního postupu. Argument je svázán pomocí výrazu, který vrací hodnotu.  
  
## <a name="variables"></a>Proměnné  
 Proměnné jsou umístění úložiště pro data. Proměnné jsou deklarovány jako součást definice pracovního postupu. Proměnné přebírají hodnoty za běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu. Definice proměnné určuje typ proměnné a volitelně i název. Následující kód ukazuje, jak deklarovat proměnnou, přiřadit jí hodnotu pomocí <xref:System.Activities.Statements.Assign%601> aktivity a pak zobrazit její hodnotu v konzole s použitím <xref:System.Activities.Statements.WriteLine> aktivity.  
  
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
  
 Výraz výchozí hodnoty lze volitelně zadat jako součást deklarace proměnné. Proměnné mohou mít také modifikátory. Například pokud je proměnná jen pro čtení, <xref:System.Activities.VariableModifiers> lze použít modifikátor jen pro čtení. V následujícím příkladu je vytvořena proměnná jen pro čtení, která má přiřazenou výchozí hodnotu.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Rozsah proměnné  
 Doba života proměnné za běhu se rovná době životnosti aktivity, která je deklaruje. Po dokončení aktivity se vyčistí její proměnné a již na ně nelze odkazovat.  
  
## <a name="arguments"></a>Arguments  
 Autoři aktivit používají argumenty k definování způsobu, jakým se data budou natékat do aktivity a z ní. Každý argument má určený směr: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> nebo <xref:System.Activities.ArgumentDirection.InOut> .  
  
 Modul runtime pracovního postupu poskytuje následující záruky týkající se časování přesunu dat do aktivit a mimo ně:  
  
1. Při zahájení aktivity se vypočítají hodnoty všech vstupních a vstupních/výstupních argumentů. Například bez ohledu na to, kdy <xref:System.Activities.Argument.Get%2A> je volána, je vrácená hodnota ta, kterou vypočítal modul runtime před jeho vyvoláním `Execute` .  
  
2. Když <xref:System.Activities.InOutArgument%601.Set%2A> je volána, modul runtime hodnotu nastaví okamžitě.  
  
3. Argumenty mohou být volitelně <xref:System.Activities.Argument.EvaluationOrder%2A> zadány. <xref:System.Activities.Argument.EvaluationOrder%2A>je hodnota založená na nule, která určuje pořadí, ve kterém je argument vyhodnocen. Ve výchozím nastavení není pořadí vyhodnocování argumentu určeno a je rovno <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> hodnotě. Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> na hodnotu větší nebo rovnou nule a určete pořadí vyhodnocování pro tento argument. Programovací model Windows Workflow Foundation vyhodnotí argumenty se zadaným pořadím vyhodnocení ve vzestupném pořadí. Všimněte si, že argumenty s nespecifikovaným pořadím hodnocení jsou vyhodnoceny před hodnotami se zadaným pořadím vyhodnocení.  
  
 Autor aktivity může použít mechanismus silného typu k odhalení svých argumentů. Toho lze dosáhnout deklarováním vlastností typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> a <xref:System.Activities.InOutArgument%601> . To umožňuje autorovi aktivity navázat konkrétní kontrakt na data, která se budou překládat do aktivity a z ní.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definování argumentů aktivity  
 Argumenty lze definovat u aktivity zadáním vlastností typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> a <xref:System.Activities.InOutArgument%601> . Následující kód ukazuje, jak definovat argumenty pro `Prompt` aktivitu, která přebírá řetězec, který se má zobrazit uživateli, a vrátí řetězec, který obsahuje odpověď uživatele.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Aktivity, které vracejí jednu hodnotu, mohou být odvozeny z <xref:System.Activities.Activity%601> , <xref:System.Activities.NativeActivity%601> nebo <xref:System.Activities.CodeActivity%601> . Tyto aktivity mají dobře definovaný <xref:System.Activities.OutArgument%601> název <xref:System.Activities.Activity%601.Result%2A> , který obsahuje vrácenou hodnotu aktivity.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Použití proměnných a argumentů v pracovních postupech  
 Následující příklad ukazuje, jak jsou proměnné a argumenty použity v pracovním postupu. Pracovní postup je sekvence, která deklaruje tři proměnné: `var1` , `var2` a `var3` . První aktivita v pracovním postupu je `Assign` aktivita, která přiřazuje hodnotu proměnné `var1` proměnné `var2` . Následuje `WriteLine` aktivita, která tiskne hodnotu `var2` proměnné. Dále je další `Assign` aktivita, která přiřadí hodnotu proměnné proměnné `var2` `var3` . Nakonec je k dispozici jiná `WriteLine` aktivita, která vytiskne hodnotu `var3` proměnné. První `Assign` aktivita používá `InArgument<string>` a `OutArgument<string>` objekty, které explicitně reprezentují vazby pro argumenty aktivity. `InArgument<string>`používá se pro <xref:System.Activities.Statements.Assign.Value%2A> , protože hodnota je předávána do <xref:System.Activities.Statements.Assign%601> aktivity pomocí jejího <xref:System.Activities.Statements.Assign.Value%2A> argumentu a `OutArgument<string>` používá se pro, <xref:System.Activities.Statements.Assign.To%2A> protože hodnota je předávána z <xref:System.Activities.Statements.Assign.To%2A> argumentu do proměnné. Druhá `Assign` aktivita dosahuje stejné věci s více kompaktní, ale ekvivalentní syntaxí, která používá implicitní přetypování. `WriteLine`Aktivity také používají syntaxi Compact.  
  
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
 Předchozí příklady ukazují, jak používat argumenty a proměnné v pracovních postupech a deklarativních aktivitách. Argumenty a proměnné jsou také používány v aktivitách založených na kódu. Konceptuální využití je velmi podobné. Proměnné představují úložiště dat v rámci aktivity a argumenty představují tok dat do nebo z aktivity a jsou vázány autorem pracovního postupu na jiné proměnné nebo argumenty v pracovním postupu, které představují, kde data přecházejí do nebo z. Chcete-li získat nebo nastavit hodnotu proměnné nebo argumentu v aktivitě, musí být použit kontext aktivity, který představuje aktuální spouštěcí prostředí aktivity. Toto je předáno do <xref:System.Activities.CodeActivity%601.Execute%2A> metody aktivity modulem runtime pracovního postupu. V tomto příkladu `Add` je definována vlastní aktivita, která má dva <xref:System.Activities.ArgumentDirection.In> argumenty. Pro přístup k hodnotě argumentů je <xref:System.Activities.Argument.Get%2A> použita metoda a je použit kontext, který byl předán modulem runtime pracovního postupu.  
  
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
  
 Další informace o práci s argumenty, proměnnými a výrazy v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [vyžadovaných argumentů a přetížených skupin](required-arguments-and-overload-groups.md).
