---
title: Interpretace výrazů
description: Naučte se psát kód pro kontrolu struktury stromu výrazů.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: fcc16e7a0cef7b3ac24d99ccbddd93bed100a5bb
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202968"
---
# <a name="interpreting-expressions"></a>Interpretace výrazů

[Předchozí výrazy, které se spouštějí](expression-trees-execution.md)

Nyní napíšeme nějaký kód pro prověření struktury *stromu výrazů*. Každý uzel ve stromové struktuře výrazu bude objektem třídy, která je odvozena z `Expression`.

Tento návrh usnadňuje návštěvu všech uzlů ve stromu výrazů a poměrně rovnou rekurzivní operaci dopřednou. Obecnou strategií je začít na kořenovém uzlu a určit, jaký typ uzlu je.

Pokud uzel má podřízené položky, rekurzivně navštíví podřízené objekty. V každém podřízeném uzlu opakujte proces použitý v kořenovém uzlu: určení typu, a pokud má typ podřízené, navštivte jednotlivé podřízené položky.

## <a name="examining-an-expression-with-no-children"></a>Zkoumání výrazu bez podřízených
Pojďme začít návštěvou každého uzlu ve vysoce jednoduchém stromu výrazu.
Zde je kód, který vytvoří konstantní výraz a pak prověřuje jeho vlastnosti:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Vytiskne se následující:

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Nyní napíšeme kód, který by prozkoumal tento výraz, a vypíšeme z něj některé důležité vlastnosti. Zde je tento kód:

## <a name="examining-a-simple-addition-expression"></a>Prozkoumání jednoduchého výrazu sčítání

Pojďme začít s ukázkou sčítání z úvodu do této části.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nepoužívám `var` deklaraci tohoto stromu výrazů, protože není možné, protože pravá strana přiřazení je implicitně typu. Pro pochopení tohoto příkladu si přečtěte [](implicitly-typed-lambda-expressions.md)toto téma.

Kořenový uzel je `LambdaExpression`. Aby bylo možné získat zajímavý kód na pravé straně `=>` operátoru, je nutné najít jeden z podřízených objektů. `LambdaExpression` Provedeme to se všemi výrazy v této části. Nadřazený uzel nám pomohly najít návratový typ `LambdaExpression`.

Abychom prozkoumali jednotlivé uzly v tomto výrazu, budeme muset rekurzivně navštívit několik uzlů. Tady je jednoduchá první implementace:

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

Tato ukázka vytiskne následující výstup:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

Ve výše uvedeném příkladu kódu si všimnete spousty opakování.
Pojďme vyčistit a vytvořit obecnější návštěvníka uzlu výrazu pro obecné účely. To bude vyžadovat, abychom napsali rekurzivní algoritmus. Libovolný uzel může být typu, který může mít podřízené objekty.
Všechny uzly, které mají podřízené objekty, vyžadují, aby nás navštívili tyto podřízené položky a určili, co je tento uzel. Zde je vyčištěná verze, která využívá rekurzi k návštěvě operací sčítání:

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

Tento algoritmus je základem algoritmu, který může libovolně navštívit libovolný `LambdaExpression`objekt. Existuje spousta děr, což znamená, že kód, který jsem vytvořil, vyhledává jenom velmi malý vzorek možných sad uzlů stromu výrazů, ke kterým může dojít. Stále ale můžete zjistit, jak trochu z toho vyprodukuje. (Výchozí případ v `Visitor.CreateFromExpression` metodě vytiskne zprávu do chybové konzoly při zjištění nového typu uzlu. Tímto způsobem víte, že chcete přidat nový typ výrazu.)

Po spuštění tohoto návštěvníka na výše uvedeném výrazu sčítání získáte následující výstup:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

Teď, když jste vytvořili obecnější implementaci návštěvníka, můžete navštívit a zpracovat spoustu více různých typů výrazů.

## <a name="examining-an-addition-expression-with-many-levels"></a>Zkoumání výrazu sčítání s mnoha úrovněmi

Pojďme si vyzkoušet složitější příklad, stále ale omezit typy uzlů jenom na sčítání:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Před spuštěním tohoto algoritmu pro návštěvníky Vyzkoušejte myšlenkový postup, který bude fungovat jako výstup. Uvědomte si `+` , že operátor je *binární operátor*: musí mít dvě podřízené prvky, reprezentující levý a pravý operand. Existuje několik možných způsobů, jak vytvořit stromovou strukturu, která může být správná:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

V případě, že se chcete podívat na nejvíc vyslibování, můžete zobrazit rozdělení na dvě možné odpovědi. První představuje *pravé asociativní* výrazy. Druhý představuje *levé asociativní* výrazy.
Výhodou obou obou formátů je, že formát se škáluje libovolným počtem výrazů sčítání. 

Pokud tento výraz spouštíte prostřednictvím návštěvníka, zobrazí se tento výstup a ověří se, jestli je výraz jednoduchého přidání *ponechán asociativní*. 

Chcete-li spustit tuto ukázku a zobrazit úplný strom výrazů, je nutné provést jednu změnu stromu zdrojového výrazu. Pokud strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnotu `10`. Kompilátor provede veškeré přidání a zmenší výraz na jeho nejjednodušší formu. Stačí přidat jednu proměnnou ve výrazu stačí k zobrazení původního stromu:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Vytvořte návštěvníka tohoto součtu a spusťte návštěvníka, na který se zobrazí tento výstup:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

Můžete také spustit libovolný z dalších ukázek prostřednictvím kódu návštěvníka a zjistit, který strom představuje. Zde je příklad `sum3` výše uvedeného výrazu (s dalším parametrem, který zabrání kompilátoru v výpočtu konstanty):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Tady je výstup návštěvníka:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

Všimněte si, že kulaté závorky nejsou součástí výstupu. Ve stromové struktuře výrazu nejsou žádné uzly, které představují závorky ve vstupním výrazu. Struktura stromu výrazů obsahuje všechny informace potřebné pro komunikaci s prioritou.

## <a name="extending-from-this-sample"></a>Rozšíření z této ukázky

Ukázka se zabývá pouze základní stromy výrazů. Kód, který jste viděli v této části, zpracovává pouze konstantní celá čísla a binární `+` operátor. Jako poslední ukázka Pojďme aktualizovat návštěvníka na zpracování složitějšího výrazu. Pojďme na to, aby to fungovalo:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Tento kód představuje jednu možnou implementaci funkce matematického *faktoriál* . Způsob, jakým jsem tento kód napsal, zvýrazní dvě omezení pro vytváření stromů výrazů přiřazením výrazů lambda výrazům. První příkazy výrazy lambda nejsou povolené. To znamená, že nemůžu použít smyčky, bloky, příkazy if/else a další řídicí struktury, které jsou C#společné v. Je omezeno na použití výrazů. Za druhé nelze rekurzivně volat stejný výraz.
Můžu se už delegovat, ale nemůžu ho zavolat ve formuláři jeho stromu výrazu. V části o sestavování [stromů výrazů](expression-trees-building.md) se naučíte techniky, jak překonat tato omezení.

V tomto výrazu se setkáte s uzly všech těchto typů:
1. EQUAL (binární výraz)
2. Násobení (binární výraz)
3. Podmíněný (? vyjádření
4. Výraz volání metody (volání `Range()` a `Aggregate()`)

Jedním ze způsobů, jak změnit algoritmus návštěvníka, je zachovat jeho spuštění a napsat typ uzlu při každém dosažení `default` klauzule. Po několika iteracích se vám podíváte na každý z možných uzlů. Pak budete mít všechno, co potřebujete. Výsledek by byl podobný tomuto:

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

ConditionalVisitor a MethodCallVisitor zpracují tyto dva uzly:

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

A výstup pro strom výrazu by byl:

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a>Rozšíření knihovny ukázek

Ukázky v této části znázorňují základní postupy pro návštěvě a prohlédnutí uzlů ve stromu výrazů. V rámci řady akcí může být nutné se soustředit na základní úlohy při návštěvě a přístupu k uzlům ve stromu výrazů. 

Nejprve Návštěvníci zpracovávají pouze konstanty, které jsou celá čísla. Konstantní hodnoty mohou být jakékoli jiné číselné typy a C# jazyk podporuje převody a propagační akce mezi těmito typy. Robustnější verze tohoto kódu by znamenala zrcadlení všech možností.

I poslední příklad rozpozná podmnožinu možných typů uzlů.
Můžete si i nadále zaniknout mnoho výrazů, které způsobí selhání.
Úplná implementace je obsažena v .NET Standard pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a může zpracovat všechny možné typy uzlů.

Nakonec se knihovna, kterou jste použili v tomto článku, vytvořila pro účely ukázky a učení. Není optimalizovaná. Napsal jsem si, že se tyto struktury využívaly velmi jasné, a zvýraznit techniky používané k návštěvě uzlů a analyzovat, co je tam. Implementace v produkčním prostředí by měla věnovat větší pozornost výkonu, než mám.

I s těmito omezeními byste měli být na cestě, jak píšete algoritmy, které čtou a porozumět stromům výrazů.

[Další – sestavování výrazů](expression-trees-building.md)
