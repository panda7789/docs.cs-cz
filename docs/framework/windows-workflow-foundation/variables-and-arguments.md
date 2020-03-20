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
# <a name="variables-and-arguments"></a><span data-ttu-id="bb847-102">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="bb847-102">Variables and Arguments</span></span>
<span data-ttu-id="bb847-103">V základech pracovních postupů systému Windows (WF) představují proměnné ukládání dat a argumenty tok dat do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="bb847-104">Aktivita má sadu argumentů a tvoří podpis aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="bb847-105">Kromě toho aktivita může udržovat seznam proměnných, ke kterým může vývojář přidávat nebo odebírat proměnné během návrhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="bb847-106">Argument je vázán pomocí výrazu, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bb847-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="bb847-107">Proměnné</span><span class="sxs-lookup"><span data-stu-id="bb847-107">Variables</span></span>  
 <span data-ttu-id="bb847-108">Proměnné jsou umístění úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="bb847-108">Variables are storage locations for data.</span></span> <span data-ttu-id="bb847-109">Proměnné jsou deklarovány jako součást definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="bb847-110">Proměnné přebírají hodnoty za běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="bb847-111">Definice proměnné určuje typ proměnné a volitelně název.</span><span class="sxs-lookup"><span data-stu-id="bb847-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="bb847-112">Následující kód ukazuje, jak deklarovat proměnnou, <xref:System.Activities.Statements.Assign%601> přiřadit hodnotu k ní pomocí <xref:System.Activities.Statements.WriteLine> aktivity a potom zobrazit jeho hodnotu konzoly pomocí aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="bb847-113">Výraz výchozí hodnoty lze volitelně zadat jako součást deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="bb847-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="bb847-114">Proměnné mohou mít také modifikátory.</span><span class="sxs-lookup"><span data-stu-id="bb847-114">Variables also can have modifiers.</span></span> <span data-ttu-id="bb847-115">Například pokud je proměnná jen pro čtení, pak lze použít modifikátor jen pro <xref:System.Activities.VariableModifiers> čtení.</span><span class="sxs-lookup"><span data-stu-id="bb847-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="bb847-116">V následujícím příkladu je vytvořena proměnná jen pro čtení, která má přiřazenou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bb847-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="bb847-117">Posunutí proměnných</span><span class="sxs-lookup"><span data-stu-id="bb847-117">Variable Scoping</span></span>  
 <span data-ttu-id="bb847-118">Životnost proměnné za běhu se rovná životnosti aktivity, která ji deklaruje.</span><span class="sxs-lookup"><span data-stu-id="bb847-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="bb847-119">Po dokončení aktivity jsou její proměnné vyčištěny a již nelze na ně odkazovat.</span><span class="sxs-lookup"><span data-stu-id="bb847-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="bb847-120">Argumenty</span><span class="sxs-lookup"><span data-stu-id="bb847-120">Arguments</span></span>  
 <span data-ttu-id="bb847-121">Autoři aktivity používají argumenty k definování způsobu toku dat do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="bb847-122">Každý argument má zadaný směr: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, nebo <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="bb847-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="bb847-123">Modul runtime pracovního postupu poskytuje následující záruky o načasování přesunu dat do a z aktivit:</span><span class="sxs-lookup"><span data-stu-id="bb847-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="bb847-124">Když aktivita spustí, hodnoty všech jeho vstupní a vstupní/výstupní argumenty jsou vypočteny.</span><span class="sxs-lookup"><span data-stu-id="bb847-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="bb847-125">Například bez ohledu <xref:System.Activities.Argument.Get%2A> na to, kdy je volána, je vrácená hodnota `Execute`hodnota vypočtená za běhu před jeho vyvoláním .</span><span class="sxs-lookup"><span data-stu-id="bb847-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="bb847-126">Při <xref:System.Activities.InOutArgument%601.Set%2A> volání, runtime nastaví hodnotu okamžitě.</span><span class="sxs-lookup"><span data-stu-id="bb847-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="bb847-127">Argumenty mohou mít <xref:System.Activities.Argument.EvaluationOrder%2A> volitelně zadaná.</span><span class="sxs-lookup"><span data-stu-id="bb847-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="bb847-128"><xref:System.Activities.Argument.EvaluationOrder%2A>je hodnota založená na nule, která určuje pořadí, ve kterém je argument vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="bb847-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="bb847-129">Ve výchozím nastavení pořadí vyhodnocení argumentu není určeno <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> a rovná se hodnotě.</span><span class="sxs-lookup"><span data-stu-id="bb847-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="bb847-130">Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> hodnotu větší nebo rovnou nule pro určení pořadí hodnocení pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="bb847-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="bb847-131">Windows Workflow Foundation vyhodnocuje argumenty se zadaným pořadím hodnocení ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bb847-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="bb847-132">Všimněte si, že argumenty s nespecifikovanou pořadí hodnocení jsou vyhodnoceny před těmi, s zadané pořadí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="bb847-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="bb847-133">Autor aktivity může použít mechanismus silného typu pro vystavení jeho argumenty.</span><span class="sxs-lookup"><span data-stu-id="bb847-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="bb847-134">Toho lze dosáhnout deklarováním <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>vlastností <xref:System.Activities.InOutArgument%601>typu , a .</span><span class="sxs-lookup"><span data-stu-id="bb847-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="bb847-135">To umožňuje autorovi aktivity vytvořit konkrétní smlouvu o datech, která přecvádějí do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="bb847-136">Definování argumentů pro aktivitu</span><span class="sxs-lookup"><span data-stu-id="bb847-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="bb847-137">Argumenty lze definovat na aktivitu zadáním <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>vlastností <xref:System.Activities.InOutArgument%601>typu , a .</span><span class="sxs-lookup"><span data-stu-id="bb847-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="bb847-138">Následující kód ukazuje, jak definovat argumenty pro aktivitu, `Prompt` která trvá v řetězci zobrazit uživateli a vrátí řetězec, který obsahuje odpověď uživatele.</span><span class="sxs-lookup"><span data-stu-id="bb847-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="bb847-139">Aktivity, které vracejí jednu hodnotu, mohou být odvozeny z , <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>, nebo <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="bb847-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="bb847-140">Tyto aktivity mají <xref:System.Activities.OutArgument%601> dobře <xref:System.Activities.Activity%601.Result%2A> definovaný název, který obsahuje vrácenou hodnotu aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="bb847-141">Použití proměnných a argumentů v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="bb847-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="bb847-142">Následující příklad ukazuje, jak se proměnné a argumenty používají v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="bb847-143">Pracovní postup je posloupnost, která `var1` `var2`deklaruje tři proměnné: , a `var3`.</span><span class="sxs-lookup"><span data-stu-id="bb847-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="bb847-144">První aktivita v pracovním `Assign` postupu je aktivita, `var1` která `var2`přiřazuje hodnotu proměnné proměnné .</span><span class="sxs-lookup"><span data-stu-id="bb847-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="bb847-145">Následuje aktivita, `WriteLine` která vytiskne `var2` hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="bb847-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="bb847-146">Další je `Assign` další aktivita, která `var2` přiřazuje hodnotu proměnné proměnné `var3`.</span><span class="sxs-lookup"><span data-stu-id="bb847-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="bb847-147">Nakonec je `WriteLine` další aktivita, která `var3` vytiskne hodnotu proměnné.</span><span class="sxs-lookup"><span data-stu-id="bb847-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="bb847-148">První `Assign` aktivita `InArgument<string>` `OutArgument<string>` používá a objekty, které explicitně představují vazby pro argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="bb847-149">`InArgument<string>`se používá <xref:System.Activities.Statements.Assign.Value%2A> pro, protože hodnota <xref:System.Activities.Statements.Assign%601> proudí <xref:System.Activities.Statements.Assign.Value%2A> do `OutArgument<string>` aktivity <xref:System.Activities.Statements.Assign.To%2A> prostřednictvím jeho argument a <xref:System.Activities.Statements.Assign.To%2A> slouží pro, protože hodnota je toku z argumentu do proměnné.</span><span class="sxs-lookup"><span data-stu-id="bb847-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="bb847-150">Druhá `Assign` aktivita provádí stejnou věc s kompaktnější, ale ekvivalentní syntaxe, která používá implicitní přetypován.</span><span class="sxs-lookup"><span data-stu-id="bb847-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="bb847-151">Aktivity `WriteLine` také použít kompaktní syntaxi.</span><span class="sxs-lookup"><span data-stu-id="bb847-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="bb847-152">Použití proměnných a argumentů v aktivitách založených na kódu</span><span class="sxs-lookup"><span data-stu-id="bb847-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="bb847-153">Předchozí příklady ukazují, jak používat argumenty a proměnné v pracovních postupech a deklarativních aktivitách.</span><span class="sxs-lookup"><span data-stu-id="bb847-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="bb847-154">Argumenty a proměnné se také používají v aktivitách založených na kódu.</span><span class="sxs-lookup"><span data-stu-id="bb847-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="bb847-155">Koncepčně použití je velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="bb847-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="bb847-156">Proměnné představují ukládání dat v rámci aktivity a argumenty představují tok dat do nebo z aktivity a jsou vázány autorem pracovního postupu na jiné proměnné nebo argumenty v pracovním postupu, které představují, kde data toky do nebo z.</span><span class="sxs-lookup"><span data-stu-id="bb847-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="bb847-157">Chcete-li získat nebo nastavit hodnotu proměnné nebo argumentu v aktivitě, musí být použit kontext aktivity, který představuje aktuální prostředí provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="bb847-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="bb847-158">To je předáno <xref:System.Activities.CodeActivity%601.Execute%2A> do metody aktivity za běhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="bb847-159">V tomto příkladu `Add` je definována <xref:System.Activities.ArgumentDirection.In> vlastní aktivita, která má dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="bb847-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="bb847-160">Pro přístup k hodnotě argumentů se používá <xref:System.Activities.Argument.Get%2A> metoda a kontext, který byl předán v běhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="bb847-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="bb847-161">Další informace o práci s argumenty, proměnnými a výrazy v kódu naleznete v [tématu Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [požadovaných argumentů a skupin přetížení](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="bb847-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
