---
title: Proměnné a argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 6e534a54802228d6d001838008fc9d8f36fc0827
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717814"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="83daf-102">Proměnné a argumenty</span><span class="sxs-lookup"><span data-stu-id="83daf-102">Variables and Arguments</span></span>
<span data-ttu-id="83daf-103">Ve Windows Workflow Foundation (WF), proměnné představují úložiště dat a argumenty představují tok dat do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-103">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="83daf-104">Aktivita má sadu argumentů a tvoří podpis aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-104">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="83daf-105">Kromě toho aktivita můžete udržovat seznam proměnných, do kterých Vývojář můžete přidávat nebo odebírat proměnné při návrhu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-105">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="83daf-106">Argument je vázán vlastnosti autorefresh pomocí výrazu, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83daf-106">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="83daf-107">Proměnné</span><span class="sxs-lookup"><span data-stu-id="83daf-107">Variables</span></span>  
 <span data-ttu-id="83daf-108">Proměnné jsou umístění úložiště pro data.</span><span class="sxs-lookup"><span data-stu-id="83daf-108">Variables are storage locations for data.</span></span> <span data-ttu-id="83daf-109">Proměnné jsou deklarovány jako součást definice pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-109">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="83daf-110">Využijte proměnné na hodnoty v době běhu a tyto hodnoty jsou uloženy jako součást stavu instance pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-110">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="83daf-111">Definice proměnné určuje typ proměnné a volitelně také název.</span><span class="sxs-lookup"><span data-stu-id="83daf-111">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="83daf-112">Následující kód ukazuje, jak deklarovat proměnné, přiřadit hodnotu pomocí <xref:System.Activities.Statements.Assign%601> aktivitu a zobrazte její hodnotu na pomocí konzoly <xref:System.Activities.Statements.WriteLine> aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-112">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
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
  
 <span data-ttu-id="83daf-113">Volitelně můžete zadat výraz výchozí hodnoty jako součást deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="83daf-113">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="83daf-114">Proměnné také můžete mít modifikátory.</span><span class="sxs-lookup"><span data-stu-id="83daf-114">Variables also can have modifiers.</span></span> <span data-ttu-id="83daf-115">Pro příklad, pokud je proměnná jen pro čtení a jen pro čtení <xref:System.Activities.VariableModifiers> lze použít modifikátor.</span><span class="sxs-lookup"><span data-stu-id="83daf-115">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="83daf-116">V následujícím příkladu se vytvoří proměnnou jen pro čtení, který má přiřazenu výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83daf-116">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="83daf-117">Proměnná rozsahu</span><span class="sxs-lookup"><span data-stu-id="83daf-117">Variable Scoping</span></span>  
 <span data-ttu-id="83daf-118">Životnost proměnné v době běhu je rovna hodnotě doba života aktivity, která jej deklaruje.</span><span class="sxs-lookup"><span data-stu-id="83daf-118">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="83daf-119">Po dokončení aktivity své proměnné se vyčistí a můžete se už neodkazuje.</span><span class="sxs-lookup"><span data-stu-id="83daf-119">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="83daf-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="83daf-120">Arguments</span></span>  
 <span data-ttu-id="83daf-121">Autoři aktivity používat argumenty pro definování dat, způsob putuje do a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-121">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="83daf-122">Každý argument má směr zadaný: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, nebo <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="83daf-122">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="83daf-123">Modul workflow runtime zaručuje následující skutečnosti o časování přesun dat do a z aktivity:</span><span class="sxs-lookup"><span data-stu-id="83daf-123">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1.  <span data-ttu-id="83daf-124">Při spuštění aktivity spuštění se počítají hodnoty všech argumentů vstupu a vstupu a výstupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-124">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="83daf-125">Například, bez ohledu na to při <xref:System.Activities.Argument.Get%2A> je volána, vrácená hodnota se počítá ten modulem runtime před jeho vyvolání `Execute`.</span><span class="sxs-lookup"><span data-stu-id="83daf-125">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2.  <span data-ttu-id="83daf-126">Když <xref:System.Activities.InOutArgument%601.Set%2A> je volána, modul runtime nastaví hodnotu okamžitě.</span><span class="sxs-lookup"><span data-stu-id="83daf-126">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3.  <span data-ttu-id="83daf-127">Argumenty můžou mít svoje <xref:System.Activities.Argument.EvaluationOrder%2A> zadané.</span><span class="sxs-lookup"><span data-stu-id="83daf-127">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="83daf-128"><xref:System.Activities.Argument.EvaluationOrder%2A> je založený na nule hodnotu, která určuje pořadí, ve kterém je vyhodnocen argument.</span><span class="sxs-lookup"><span data-stu-id="83daf-128"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="83daf-129">Ve výchozím nastavení, pořadí vyhodnocení argumentu není zadána a je rovna <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="83daf-129">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="83daf-130">Nastavte <xref:System.Activities.Argument.EvaluationOrder%2A> na hodnotu větší nebo rovna hodnotě nula. Chcete-li určit pořadí vyhodnocení pro tento argument.</span><span class="sxs-lookup"><span data-stu-id="83daf-130">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="83daf-131">Windows Workflow Foundation vyhodnotí argumentů s pořadím vyhodnocení zadané ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="83daf-131">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="83daf-132">Všimněte si, že před těmi, které mají zadanou evaluationorder jsou vyhodnoceny argumenty s objednávkou neurčené hodnocení.</span><span class="sxs-lookup"><span data-stu-id="83daf-132">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="83daf-133">Autor aktivity můžete použít mechanismus silného typu pro vystavení svých argumentů.</span><span class="sxs-lookup"><span data-stu-id="83daf-133">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="83daf-134">Toho lze dosáhnout deklarování vlastností typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="83daf-134">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="83daf-135">To umožňuje autorovi aktivity stanovit konkrétní smlouvy o data přicházející do proměnné a z aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-135">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="83daf-136">Definování argumenty pro aktivitu</span><span class="sxs-lookup"><span data-stu-id="83daf-136">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="83daf-137">Argumenty můžete definovat pro aktivitu tak, že zadáte vlastnosti typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, a <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="83daf-137">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="83daf-138">Následující kód ukazuje, jak definovat argumenty `Prompt` aktivitu, která přijímá řetězec k zobrazení pro uživatele a vrátí řetězec, který obsahuje odpověď uživatele.</span><span class="sxs-lookup"><span data-stu-id="83daf-138">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="83daf-139">Aktivity, které vrátí jednu hodnotu lze odvodit z <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, nebo <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="83daf-139">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="83daf-140">Tyto aktivity mají jasně definovaných <xref:System.Activities.OutArgument%601> s názvem <xref:System.Activities.Activity%601.Result%2A> , který obsahuje vrácenou hodnotu aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-140">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="83daf-141">Použití proměnných a argumentů v pracovních postupech</span><span class="sxs-lookup"><span data-stu-id="83daf-141">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="83daf-142">Následující příklad ukazuje, jak proměnné a argumenty se používají v pracovním postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-142">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="83daf-143">Pracovní postup je sekvence, která deklaruje tří proměnných: `var1`, `var2`, a `var3`.</span><span class="sxs-lookup"><span data-stu-id="83daf-143">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="83daf-144">První aktivitu v pracovním postupu je `Assign` aktivity, který přiřazuje hodnotu proměnné `var1` proměnné `var2`.</span><span class="sxs-lookup"><span data-stu-id="83daf-144">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="83daf-145">Následuje `WriteLine` aktivitu, která vytiskne hodnotu `var2` proměnné.</span><span class="sxs-lookup"><span data-stu-id="83daf-145">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="83daf-146">Dále je další `Assign` aktivity, který přiřazuje hodnotu proměnné `var2` proměnné `var3`.</span><span class="sxs-lookup"><span data-stu-id="83daf-146">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="83daf-147">Nakonec je jiný `WriteLine` aktivitu, která vytiskne hodnotu `var3` proměnné.</span><span class="sxs-lookup"><span data-stu-id="83daf-147">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="83daf-148">První `Assign` používá aktivitu `InArgument<string>` a `OutArgument<string>` objekty, které explicitně představují vazby pro argumenty aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-148">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="83daf-149">`InArgument<string>` slouží k <xref:System.Activities.Statements.Assign.Value%2A> vzhledem k tomu, že hodnota se přenášejí do <xref:System.Activities.Statements.Assign%601> aktivity prostřednictvím jeho <xref:System.Activities.Statements.Assign.Value%2A> argument, a `OutArgument<string>` se používá pro <xref:System.Activities.Statements.Assign.To%2A> vzhledem k tomu, že hodnota se přenášejí z celkového počtu <xref:System.Activities.Statements.Assign.To%2A> argument do proměnné.</span><span class="sxs-lookup"><span data-stu-id="83daf-149">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="83daf-150">Druhá `Assign` aktivity totéž provede další compact ale ekvivalentní syntax, který používá implicitní přetypování.</span><span class="sxs-lookup"><span data-stu-id="83daf-150">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="83daf-151">`WriteLine` Aktivity také používají nejúspornější syntaxí.</span><span class="sxs-lookup"><span data-stu-id="83daf-151">The `WriteLine` activities also use the compact syntax.</span></span>  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="83daf-152">Pomocí proměnné a argumenty aktivity založený na kódu</span><span class="sxs-lookup"><span data-stu-id="83daf-152">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="83daf-153">Předchozí příklady ukazují, jak používat argumenty a proměnných v pracovních postupech a deklarativní aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-153">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="83daf-154">Proměnné a argumenty se používají také v aktivity založený na kódu.</span><span class="sxs-lookup"><span data-stu-id="83daf-154">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="83daf-155">Využití je obecně velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="83daf-155">Conceptually the usage is very similar.</span></span> <span data-ttu-id="83daf-156">Proměnné představují úložiště dat v rámci aktivity a argumenty představují tok dat do nebo z něj aktivity a jsou vázány, které představují, kde se data posílají do nebo z jiných proměnných nebo argumentů v pracovním postupu Autor pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-156">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="83daf-157">Chcete-li get nebo set, použita hodnota proměnné nebo argumentu do aktivity, objekt context aktivita, která představuje aktuální prostředí provádění aktivity.</span><span class="sxs-lookup"><span data-stu-id="83daf-157">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="83daf-158">To je předán <xref:System.Activities.CodeActivity%601.Execute%2A> metodu činnosti pomocí modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-158">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="83daf-159">V tomto příkladu vlastní `Add` aktivity je definován, která má dvě <xref:System.Activities.ArgumentDirection.In> argumenty.</span><span class="sxs-lookup"><span data-stu-id="83daf-159">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="83daf-160">Pro přístup k hodnotě argumenty, <xref:System.Activities.Argument.Get%2A> metoda se používá a je použit kontext, který byl předán pomocí modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="83daf-160">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="83daf-161">Další informace o práci s argumenty, proměnné a výrazy v kódu, naleznete v tématu [vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu](authoring-workflows-activities-and-expressions-using-imperative-code.md) a [povinné argumenty a skupiny přetížení](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="83daf-161">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
