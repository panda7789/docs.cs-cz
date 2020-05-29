---
title: Proměnné a argumenty
description: Tento článek popisuje proměnné, které reprezentují úložiště dat a argumenty, které reprezentují tok dat do/z aktivity v modelu Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 5cce9931e9b0a37d5fafbfb84527ffd543a0a50f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201947"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="7af84-103">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="7af84-103">Variables and Arguments</span></span>
<span data-ttu-id="7af84-104">V programovací model Windows Workflow Foundation (WF) proměnné reprezentují úložiště dat a argumenty představuje tok dat do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="7af84-105">Aktivita má sadu argumentů a tvoří podpis aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="7af84-106">Kromě toho aktivita může udržovat seznam proměnných, ke kterým může vývojář přidávat nebo odebírat proměnné během návrhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="7af84-107">Argument je svázán pomocí výrazu, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7af84-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="7af84-108">Proměnné</span><span class="sxs-lookup"><span data-stu-id="7af84-108">Variables</span></span>  
 <span data-ttu-id="7af84-109">Proměnné jsou umístění úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="7af84-109">Variables are storage locations for data.</span></span> <span data-ttu-id="7af84-110">Proměnné jsou deklarovány jako součást definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="7af84-111">Proměnné přebírají hodnoty za běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="7af84-112">Definice proměnné určuje typ proměnné a volitelně i název.</span><span class="sxs-lookup"><span data-stu-id="7af84-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="7af84-113">Následující kód ukazuje, jak deklarovat proměnnou, přiřadit jí hodnotu pomocí <xref:System.Activities.Statements.Assign%601> aktivity a pak zobrazit její hodnotu v konzole s použitím <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="7af84-114">Výraz výchozí hodnoty lze volitelně zadat jako součást deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="7af84-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="7af84-115">Proměnné mohou mít také modifikátory.</span><span class="sxs-lookup"><span data-stu-id="7af84-115">Variables also can have modifiers.</span></span> <span data-ttu-id="7af84-116">Například pokud je proměnná jen pro čtení, <xref:System.Activities.VariableModifiers> lze použít modifikátor jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="7af84-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="7af84-117">V následujícím příkladu je vytvořena proměnná jen pro čtení, která má přiřazenou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7af84-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="7af84-118">Rozsah proměnné</span><span class="sxs-lookup"><span data-stu-id="7af84-118">Variable Scoping</span></span>  
 <span data-ttu-id="7af84-119">Doba života proměnné za běhu se rovná době životnosti aktivity, která je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="7af84-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="7af84-120">Po dokončení aktivity se vyčistí její proměnné a již na ně nelze odkazovat.</span><span class="sxs-lookup"><span data-stu-id="7af84-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="7af84-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="7af84-121">Arguments</span></span>  
 <span data-ttu-id="7af84-122">Autoři aktivit používají argumenty k definování způsobu, jakým se data budou natékat do aktivity a z ní.</span><span class="sxs-lookup"><span data-stu-id="7af84-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="7af84-123">Každý argument má určený směr: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> nebo <xref:System.Activities.ArgumentDirection.InOut> .</span><span class="sxs-lookup"><span data-stu-id="7af84-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="7af84-124">Modul runtime pracovního postupu poskytuje následující záruky týkající se časování přesunu dat do aktivit a mimo ně:</span><span class="sxs-lookup"><span data-stu-id="7af84-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="7af84-125">Při zahájení aktivity se vypočítají hodnoty všech vstupních a vstupních/výstupních argumentů.</span><span class="sxs-lookup"><span data-stu-id="7af84-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="7af84-126">Například bez ohledu na to, kdy <xref:System.Activities.Argument.Get%2A> je volána, je vrácená hodnota ta, kterou vypočítal modul runtime před jeho vyvoláním `Execute` .</span><span class="sxs-lookup"><span data-stu-id="7af84-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="7af84-127">Když <xref:System.Activities.InOutArgument%601.Set%2A> je volána, modul runtime hodnotu nastaví okamžitě.</span><span class="sxs-lookup"><span data-stu-id="7af84-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="7af84-128">Argumenty mohou být volitelně <xref:System.Activities.Argument.EvaluationOrder%2A> zadány.</span><span class="sxs-lookup"><span data-stu-id="7af84-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="7af84-129"><xref:System.Activities.Argument.EvaluationOrder%2A>je hodnota založená na nule, která určuje pořadí, ve kterém je argument vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="7af84-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="7af84-130">Ve výchozím nastavení není pořadí vyhodnocování argumentu určeno a je rovno <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> hodnotě.</span><span class="sxs-lookup"><span data-stu-id="7af84-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="7af84-131">Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> na hodnotu větší nebo rovnou nule a určete pořadí vyhodnocování pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="7af84-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="7af84-132">Programovací model Windows Workflow Foundation vyhodnotí argumenty se zadaným pořadím vyhodnocení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7af84-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="7af84-133">Všimněte si, že argumenty s nespecifikovaným pořadím hodnocení jsou vyhodnoceny před hodnotami se zadaným pořadím vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="7af84-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="7af84-134">Autor aktivity může použít mechanismus silného typu k odhalení svých argumentů.</span><span class="sxs-lookup"><span data-stu-id="7af84-134">An activity author can use a strongly typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="7af84-135">Toho lze dosáhnout deklarováním vlastností typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> a <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="7af84-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="7af84-136">To umožňuje autorovi aktivity navázat konkrétní kontrakt na data, která se budou překládat do aktivity a z ní.</span><span class="sxs-lookup"><span data-stu-id="7af84-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="7af84-137">Definování argumentů aktivity</span><span class="sxs-lookup"><span data-stu-id="7af84-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="7af84-138">Argumenty lze definovat u aktivity zadáním vlastností typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> a <xref:System.Activities.InOutArgument%601> .</span><span class="sxs-lookup"><span data-stu-id="7af84-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="7af84-139">Následující kód ukazuje, jak definovat argumenty pro `Prompt` aktivitu, která přebírá řetězec, který se má zobrazit uživateli, a vrátí řetězec, který obsahuje odpověď uživatele.</span><span class="sxs-lookup"><span data-stu-id="7af84-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="7af84-140">Aktivity, které vracejí jednu hodnotu, mohou být odvozeny z <xref:System.Activities.Activity%601> , <xref:System.Activities.NativeActivity%601> nebo <xref:System.Activities.CodeActivity%601> .</span><span class="sxs-lookup"><span data-stu-id="7af84-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="7af84-141">Tyto aktivity mají dobře definovaný <xref:System.Activities.OutArgument%601> název <xref:System.Activities.Activity%601.Result%2A> , který obsahuje vrácenou hodnotu aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="7af84-142">Použití proměnných a argumentů v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="7af84-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="7af84-143">Následující příklad ukazuje, jak jsou proměnné a argumenty použity v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="7af84-144">Pracovní postup je sekvence, která deklaruje tři proměnné: `var1` , `var2` a `var3` .</span><span class="sxs-lookup"><span data-stu-id="7af84-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="7af84-145">První aktivita v pracovním postupu je `Assign` aktivita, která přiřazuje hodnotu proměnné `var1` proměnné `var2` .</span><span class="sxs-lookup"><span data-stu-id="7af84-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="7af84-146">Následuje `WriteLine` aktivita, která tiskne hodnotu `var2` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7af84-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="7af84-147">Dále je další `Assign` aktivita, která přiřadí hodnotu proměnné proměnné `var2` `var3` .</span><span class="sxs-lookup"><span data-stu-id="7af84-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="7af84-148">Nakonec je k dispozici jiná `WriteLine` aktivita, která vytiskne hodnotu `var3` proměnné.</span><span class="sxs-lookup"><span data-stu-id="7af84-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="7af84-149">První `Assign` aktivita používá `InArgument<string>` a `OutArgument<string>` objekty, které explicitně reprezentují vazby pro argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="7af84-150">`InArgument<string>`používá se pro <xref:System.Activities.Statements.Assign.Value%2A> , protože hodnota je předávána do <xref:System.Activities.Statements.Assign%601> aktivity pomocí jejího <xref:System.Activities.Statements.Assign.Value%2A> argumentu a `OutArgument<string>` používá se pro, <xref:System.Activities.Statements.Assign.To%2A> protože hodnota je předávána z <xref:System.Activities.Statements.Assign.To%2A> argumentu do proměnné.</span><span class="sxs-lookup"><span data-stu-id="7af84-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="7af84-151">Druhá `Assign` aktivita dosahuje stejné věci s více kompaktní, ale ekvivalentní syntaxí, která používá implicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="7af84-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="7af84-152">`WriteLine`Aktivity také používají syntaxi Compact.</span><span class="sxs-lookup"><span data-stu-id="7af84-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="7af84-153">Použití proměnných a argumentů v aktivitách založených na kódu</span><span class="sxs-lookup"><span data-stu-id="7af84-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="7af84-154">Předchozí příklady ukazují, jak používat argumenty a proměnné v pracovních postupech a deklarativních aktivitách.</span><span class="sxs-lookup"><span data-stu-id="7af84-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="7af84-155">Argumenty a proměnné jsou také používány v aktivitách založených na kódu.</span><span class="sxs-lookup"><span data-stu-id="7af84-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="7af84-156">Konceptuální využití je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="7af84-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="7af84-157">Proměnné představují úložiště dat v rámci aktivity a argumenty představují tok dat do nebo z aktivity a jsou vázány autorem pracovního postupu na jiné proměnné nebo argumenty v pracovním postupu, které představují, kde data přecházejí do nebo z.</span><span class="sxs-lookup"><span data-stu-id="7af84-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="7af84-158">Chcete-li získat nebo nastavit hodnotu proměnné nebo argumentu v aktivitě, musí být použit kontext aktivity, který představuje aktuální spouštěcí prostředí aktivity.</span><span class="sxs-lookup"><span data-stu-id="7af84-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="7af84-159">Toto je předáno do <xref:System.Activities.CodeActivity%601.Execute%2A> metody aktivity modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="7af84-160">V tomto příkladu `Add` je definována vlastní aktivita, která má dva <xref:System.Activities.ArgumentDirection.In> argumenty.</span><span class="sxs-lookup"><span data-stu-id="7af84-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="7af84-161">Pro přístup k hodnotě argumentů je <xref:System.Activities.Argument.Get%2A> použita metoda a je použit kontext, který byl předán modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="7af84-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="7af84-162">Další informace o práci s argumenty, proměnnými a výrazy v kódu naleznete v tématu [vytváření pracovních postupů, aktivity a výrazy pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [vyžadovaných argumentů a přetížených skupin](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="7af84-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
