---
title: Výrazy lambda - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 77701653abacbe6d876c0890a11586f0840bad5d
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200894"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="a0972-102">Výrazy lambda (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="a0972-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="a0972-103">Výraz lambda je [anonymní funkce](anonymous-methods.md) , můžete použít k vytvoření [delegáti](../delegates/using-delegates.md) nebo [stromu výrazů](../concepts/expression-trees/index.md) typy.</span><span class="sxs-lookup"><span data-stu-id="a0972-103">A lambda expression is an [anonymous function](anonymous-methods.md) that you can use to create [delegates](../delegates/using-delegates.md) or [expression tree](../concepts/expression-trees/index.md) types.</span></span> <span data-ttu-id="a0972-104">Pomocí výrazů lambda můžete psát místní funkce, které mohou být předány jako argumenty nebo vráceny jako hodnota volání funkce.</span><span class="sxs-lookup"><span data-stu-id="a0972-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="a0972-105">Výrazy lambda jsou zvláště užitečné pro psaní výrazů dotazů LINQ.</span><span class="sxs-lookup"><span data-stu-id="a0972-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>
  
<span data-ttu-id="a0972-106">Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda [ => ](../../../csharp/language-reference/operators/lambda-operator.md), a umístěte blok výrazu nebo příkazu na druhé straně.</span><span class="sxs-lookup"><span data-stu-id="a0972-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="a0972-107">Například výraz lambda `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci.</span><span class="sxs-lookup"><span data-stu-id="a0972-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="a0972-108">Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="a0972-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="a0972-109">Postup vytvoření typu stromu výrazu:</span><span class="sxs-lookup"><span data-stu-id="a0972-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="a0972-110">`=>` Operátor má stejnou prioritu jako přiřazení (`=`) a je [asociativní zprava](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (viz oddíl "Asociativita" operátory článku).</span><span class="sxs-lookup"><span data-stu-id="a0972-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="a0972-111">Výrazy lambda se používají v založených na volání metody [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů jako argumenty pro standardní metody operátoru dotazu, jako například <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="a0972-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="a0972-112">Při použití syntaxe založených na volání metody na volání <xref:System.Linq.Enumerable.Where%2A> metoda ve <xref:System.Linq.Enumerable> třídy (stejně jako v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] k objektům a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) je parametr typu delegáta <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a0972-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a0972-113">Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu.</span><span class="sxs-lookup"><span data-stu-id="a0972-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="a0972-114">Při volání stejné metody, například <xref:System.Linq.Queryable?displayProperty=nameWithType> třídy (stejně jako v [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) je typ parametru <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>< Func\> kde Func je libovolný delegát Func s až šestnácti vstupními parametry.</span><span class="sxs-lookup"><span data-stu-id="a0972-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="a0972-115">Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0972-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="a0972-116">Výrazy lambda umožňují `Where` volání vypadalo podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda jiný.</span><span class="sxs-lookup"><span data-stu-id="a0972-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="a0972-117">V předchozím příkladu, Všimněte si, že podpis delegáta má jeden implicitně zadaný vstupní parametr typu `int`a vrátí `int`.</span><span class="sxs-lookup"><span data-stu-id="a0972-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="a0972-118">Výraz lambda může být převeden na delegáta daného typu, protože má také jeden vstupní parametr (`x`) a návratovou hodnotu, může kompilátor implicitně převést na typ `int`.</span><span class="sxs-lookup"><span data-stu-id="a0972-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="a0972-119">(Odvození typu je popsáno podrobněji v následujících částech). Pokud je delegát vyvolán pomocí vstupního parametru 5, vrátí výsledek 25.</span><span class="sxs-lookup"><span data-stu-id="a0972-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="a0972-120">Výrazy lambda nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) nebo [jako](../../../csharp/language-reference/keywords/as.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="a0972-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="a0972-121">Všechna omezení, která platí pro anonymní metody, platí také pro výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="a0972-122">Další informace najdete v tématu [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0972-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="a0972-123">Výrazové lambdy</span><span class="sxs-lookup"><span data-stu-id="a0972-123">Expression lambdas</span></span>

 <span data-ttu-id="a0972-124">Výraz lambda s výrazem na pravé straně = > – operátor je volána *výrazu lambda*.</span><span class="sxs-lookup"><span data-stu-id="a0972-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="a0972-125">Výrazové lambdy se často používají v konstrukci [stromů výrazů](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0972-125">Expression lambdas are used extensively in the construction of [Expression Trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="a0972-126">Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:</span><span class="sxs-lookup"><span data-stu-id="a0972-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="a0972-127">Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.</span><span class="sxs-lookup"><span data-stu-id="a0972-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="a0972-128">Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:</span><span class="sxs-lookup"><span data-stu-id="a0972-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="a0972-129">Někdy je pro kompilátor obtížné či nemožné odvodit vstupní typy.</span><span class="sxs-lookup"><span data-stu-id="a0972-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="a0972-130">V takovém případě můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a0972-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```
 <span data-ttu-id="a0972-131">Vstupní parametr typy musí být všechny explicitní, nebo všechny implicitní; v opačném případě jazyka C# vygeneruje [CS0748](../../misc/cs0748.md) chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a0972-131">Input parameter types must be all explicit or all implicit; otherwise, C# generates a [CS0748](../../misc/cs0748.md) compiler error.</span></span>

 <span data-ttu-id="a0972-132">Zadejte nulové vstupní parametry s prázdnými závorkami:</span><span class="sxs-lookup"><span data-stu-id="a0972-132">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="a0972-133">V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody.</span><span class="sxs-lookup"><span data-stu-id="a0972-133">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="a0972-134">Pokud však vytváříte stromy výrazu, které jsou vyhodnocovány mimo rozhraní .NET Framework, například na SQL Server, neměli byste používat volání metody ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-134">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="a0972-135">Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a0972-135">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="a0972-136">Příkazové lambdy</span><span class="sxs-lookup"><span data-stu-id="a0972-136">Statement lambdas</span></span>

 <span data-ttu-id="a0972-137">Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:</span><span class="sxs-lookup"><span data-stu-id="a0972-137">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="a0972-138">(vstupní parametry) = > {příkaz;}</span><span class="sxs-lookup"><span data-stu-id="a0972-138">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="a0972-139">Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.</span><span class="sxs-lookup"><span data-stu-id="a0972-139">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLambda#1](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLambda#2](~/samples/snippets/csharp/programming-guide/lambda-expressions/statements.cs#2)]

 <span data-ttu-id="a0972-140">Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0972-140">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="a0972-141">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="a0972-141">Async lambdas</span></span>

 <span data-ttu-id="a0972-142">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) a [await](../../../csharp/language-reference/keywords/await.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="a0972-142">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="a0972-143">Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="a0972-143">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="a0972-144">Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy.</span><span class="sxs-lookup"><span data-stu-id="a0972-144">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="a0972-145">Chcete-li přidat tuto obslužnou rutinu, přidejte `async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a0972-145">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="a0972-146">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0972-146">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="a0972-147">Výrazy lambda s operátory standardního dotazu</span><span class="sxs-lookup"><span data-stu-id="a0972-147">Lambdas with the standard query operators</span></span>

 <span data-ttu-id="a0972-148">Mnoho standardních operátorů dotazu má vstupní parametr, jehož typ je jednou z <xref:System.Func%602> řady obecných delegátů.</span><span class="sxs-lookup"><span data-stu-id="a0972-148">Many standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="a0972-149">Tyto delegáty používají parametry typu pro definování počtu a typů vstupních parametrů a návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="a0972-149">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="a0972-150">`Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat.</span><span class="sxs-lookup"><span data-stu-id="a0972-150">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="a0972-151">Zvažte například následující typ delegátu:</span><span class="sxs-lookup"><span data-stu-id="a0972-151">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="a0972-152">Delegát může být vytvořen jako `Func<int,bool> myFunc` kde `int` je vstupní parametr a `bool` je návratová hodnota.</span><span class="sxs-lookup"><span data-stu-id="a0972-152">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="a0972-153">Vrácená hodnota je vždy určena v posledním parametru typu.</span><span class="sxs-lookup"><span data-stu-id="a0972-153">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="a0972-154">`Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="a0972-154">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="a0972-155">Následující `Func` delegáta, při vyvolání, vrátí hodnotu true nebo false označuje, zda je vstupní parametr roven hodnotě 5:</span><span class="sxs-lookup"><span data-stu-id="a0972-155">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="a0972-156">Výraz lambda lze také zadat, pokud je typ argumentu `Expression<Func>`, například ve standardních operátorech dotazu, které jsou definovány v System.Linq.Queryable.</span><span class="sxs-lookup"><span data-stu-id="a0972-156">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="a0972-157">Pokud zadáte `Expression<Func>` argument, bude lambda kompilována na strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="a0972-157">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="a0972-158">Standardní operátor dotazu, <xref:System.Linq.Enumerable.Count%2A> metoda, je znázorněna zde:</span><span class="sxs-lookup"><span data-stu-id="a0972-158">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="a0972-159">Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně.</span><span class="sxs-lookup"><span data-stu-id="a0972-159">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="a0972-160">Tento konkrétní výraz lambda vrátí ta celá čísla (`n`) která po vydělení dvěma mají zbytek 1.</span><span class="sxs-lookup"><span data-stu-id="a0972-160">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="a0972-161">Následující řádek kódu vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které jsou nalevo od hodnoty 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:</span><span class="sxs-lookup"><span data-stu-id="a0972-161">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="a0972-162">Tento příklad znázorňuje způsob zadávání většího počtu vstupních parametrů uzavřením do závorek.</span><span class="sxs-lookup"><span data-stu-id="a0972-162">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="a0972-163">Metoda vrátí všechny prvky v poli čísel, dokud není zjištěno číslo, jehož hodnota je nižší než jeho pozice.</span><span class="sxs-lookup"><span data-stu-id="a0972-163">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="a0972-164">Nezaměňujte operátor lambda (`=>`) s operátorem větší než nebo rovno (`>=`).</span><span class="sxs-lookup"><span data-stu-id="a0972-164">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="a0972-165">Odvození typu proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="a0972-165">Type inference in lambdas</span></span>

 <span data-ttu-id="a0972-166">Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní části výrazu lambda, typu delegátu parametru a dalších faktorů, jak je popsáno ve specifikaci jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="a0972-166">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="a0972-167">Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="a0972-167">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="a0972-168">Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:</span><span class="sxs-lookup"><span data-stu-id="a0972-168">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="a0972-169">Obecná pravidla pro výrazy lambda jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a0972-169">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="a0972-170">Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="a0972-170">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="a0972-171">Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.</span><span class="sxs-lookup"><span data-stu-id="a0972-171">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="a0972-172">Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.</span><span class="sxs-lookup"><span data-stu-id="a0972-172">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="a0972-173">Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“.</span><span class="sxs-lookup"><span data-stu-id="a0972-173">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="a0972-174">Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-174">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="a0972-175">V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-175">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="a0972-176">Rozsah proměnné ve výrazech lambda</span><span class="sxs-lookup"><span data-stu-id="a0972-176">Variable scope in lambda expressions</span></span>

 <span data-ttu-id="a0972-177">Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metodě, která definuje funkci lambda, nebo v rozsahu typu, který obsahuje výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-177">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="a0972-178">Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a0972-178">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="a0972-179">Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a0972-179">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="a0972-180">Následující příklad znázorňuje tato pravidla:</span><span class="sxs-lookup"><span data-stu-id="a0972-180">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="a0972-181">Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:</span><span class="sxs-lookup"><span data-stu-id="a0972-181">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="a0972-182">Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a0972-182">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="a0972-183">Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.</span><span class="sxs-lookup"><span data-stu-id="a0972-183">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="a0972-184">Výraz lambda nemůže přímo zachytit `in`, `ref`, nebo `out` parametr z ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="a0972-184">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="a0972-185">Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.</span><span class="sxs-lookup"><span data-stu-id="a0972-185">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="a0972-186">Výraz lambda nemůže obsahovat `goto` příkazu `break` příkazu, nebo `continue` příkaz, který se nachází uvnitř funkce lambda, pokud cíl příkazu skoku je mimo blok.</span><span class="sxs-lookup"><span data-stu-id="a0972-186">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="a0972-187">Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="a0972-187">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a0972-188">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0972-188">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="a0972-189">Doporučená kapitola knihy</span><span class="sxs-lookup"><span data-stu-id="a0972-189">Featured book chapter</span></span>

 <span data-ttu-id="a0972-190">[Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="a0972-190">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0972-191">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0972-191">See also</span></span>

- [<span data-ttu-id="a0972-192">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a0972-192">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a0972-193">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a0972-193">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="a0972-194">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="a0972-194">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="a0972-195">is</span><span class="sxs-lookup"><span data-stu-id="a0972-195">is</span></span>](../../../csharp/language-reference/keywords/is.md)
- [<span data-ttu-id="a0972-196">Stromy výrazů</span><span class="sxs-lookup"><span data-stu-id="a0972-196">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="a0972-197">Visual Studio 2008 C# – ukázky (viz ukázkové soubory dotazů LINQ a XQuery program)</span><span class="sxs-lookup"><span data-stu-id="a0972-197">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="a0972-198">Rekurzivní výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="a0972-198">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
