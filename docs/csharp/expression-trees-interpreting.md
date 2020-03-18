---
title: Interpretace výrazů
description: Naučte se psát kód prozkoumat strukturu stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146005"
---
# <a name="interpreting-expressions"></a>Interpretace výrazů

[Předchozí -- Provádění výrazů](expression-trees-execution.md)

Nyní napíšeme nějaký kód, který prozkoumá strukturu *stromu výrazů*. Každý uzel ve stromu výrazů bude objektem třídy, která je odvozena z `Expression`.

Tento návrh umožňuje návštěvě všech uzlů ve stromu výrazu relativně přímočaré rekurzivní operace. Obecnou strategií je začít v kořenovém uzlu a určit, jaký druh uzlu je.

Pokud typ uzlu má podřízené, rekurzivně navštivte děti. V každém podřízeném uzlu opakujte proces použitý v kořenovém uzlu: určete typ a pokud má typ podřízené děti, navštivte každou z podřízených.

## <a name="examining-an-expression-with-no-children"></a>Zkoumání výrazu bez podřízených výrazů
Začněme návštěvou každého uzlu ve velmi jednoduchém stromu výrazů.
Zde je kód, který vytvoří konstantní výraz a pak zkoumá jeho vlastnosti:

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

Nyní napíšeme kód, který by prozkoumat tento výraz a napsat některé důležité vlastnosti o něm. Tady je ten kód:

## <a name="examining-a-simple-addition-expression"></a>Zkoumání jednoduchého výrazu sčítání

Začněme s ukázkou přidání z úvodu do této části.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nepoužívám `var` k deklarování tohoto stromu výrazů, protože to není možné, protože pravá strana přiřazení je implicitně zadána. Chcete-li pochopit, že hlouběji, přečtěte si [zde](implicitly-typed-lambda-expressions.md).

Kořenový uzel je `LambdaExpression`. Chcete-li získat zajímavý kód na pravé `=>` straně operátora, musíte najít jednu `LambdaExpression`z poddajných . Uděláme to se všemi výrazy v této sekci. Nadřazený uzel nám pomáhá najít `LambdaExpression`návratový typ .

Chcete-li prozkoumat každý uzel v tomto výrazu, budeme muset rekurzivně navštívit několik uzlů. Zde je jednoduchá první implementace:

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

V ukázkové části kódu si všimnete mnoha opakování.
Pojďme vyčistit, že se a vybudovat obecnější účel výraz uzlu návštěvníka. To bude vyžadovat, abychom napsali rekurzivní algoritmus. Libovolný uzel může být typu, který může mít podřízené.
Každý uzel, který má děti vyžaduje, abychom navštívili tyto děti a určit, co tento uzel je. Zde je vyčištěna verze, která využívá rekurze k návštěvě sčítání operace:

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

Tento algoritmus je základem algoritmu, který `LambdaExpression`může navštívit libovolné . Existuje mnoho děr, a to, že kód, který jsem vytvořil, hledá pouze velmi malý vzorek možných sad uzlů stromu výrazů, se kterými se může setkat. Nicméně, stále se můžete naučit docela dost z toho, co produkuje. (Výchozí případ v `Visitor.CreateFromExpression` metodě vytiskne zprávu do konzoly chyb, když je zjištěn nový typ uzlu. Tímto způsobem víte, přidat nový typ výrazu.)

Když spustíte tohoto návštěvníka na přidání výraz uvýšený, získáte následující výstup:

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

Nyní, když jste vytvořili obecnější implementaci návštěvníků, můžete navštívit a zpracovat mnoho dalších různých typů výrazů.

## <a name="examining-an-addition-expression-with-many-levels"></a>Zkoumání výrazu sčítání s mnoha úrovněmi

Zkusme složitější příklad, ale přesto omezit typy uzlů pouze sčítání:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Než to spustíte na algoritmu návštěvníka, zkuste myšlenkové cvičení, abyste zjistili, jaký by mohl být výstup. Nezapomeňte, `+` že operátor je *binární operátor*: musí mít dvě podřízené objekty představující levé a pravé operandy. Existuje několik možných způsobů, jak vytvořit strom, který by mohl být správný:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Můžete vidět oddělení do dvou možných odpovědí upozornit na nejslibnější. První představuje *právo asociativní* výrazy. Druhý představují *levé asociativní* výrazy.
Výhodou obou těchto dvou formátů je, že formát se škáluje na libovolný počet výrazů sčítání.

Pokud spustíte tento výraz prostřednictvím návštěvníka, zobrazí se tento výstup, ověření, že jednoduchý výraz sčítání je *ponechána asociativní*.

Chcete-li spustit tuto ukázku a zobrazit celý strom výrazu, musel jsem provést jednu změnu stromu zdrojového výrazu. Pokud strom výrazu obsahuje všechny konstanty, výsledný strom `10`jednoduše obsahuje konstantní hodnotu . Kompilátor provede všechny sčítání a snižuje výraz na jeho nejjednodušší formu. Jednoduše přidání jedné proměnné ve výrazu je dostačující pro zobrazení původního stromu:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Vytvořte návštěvníka pro tuto částku a spusťte návštěvníka uvidíte tento výstup:

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

Můžete také spustit některý z dalších vzorků prostřednictvím kódu návštěvníka a zjistit, jaký strom představuje. Zde je příklad výše `sum3` uvedeného výrazu (s dalším parametrem, který zabrání kompilátoru v výpočtu konstanty):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Zde je výstup z návštěvníka:

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

Všimněte si, že závorky nejsou součástí výstupu. Ve stromu výrazů nejsou žádné uzly, které představují závorky ve vstupním výrazu. Struktura stromu výrazobsahuje všechny informace potřebné ke sdělení priority.

## <a name="extending-from-this-sample"></a>Rozšíření z tohoto vzorku

Ukázka se zabývá pouze nejvíce základní výraz stromy. Kód, který jste viděli v této části zpracovává pouze konstantní `+` celá čísla a binární operátor. Jako poslední ukázku aktualizujte návštěvníka, aby zpracovat složitější výraz. Ať to funguje na toto:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Tento kód představuje jednu možnou implementaci matematické *faktoriální* funkce. Způsob, jakým jsem napsal tento kód zvýrazní dvě omezení vytváření stromů výrazů přiřazením lambda výrazy výrazy výrazy. Za prvé, prohlášení lambdas nejsou povoleny. To znamená, že nelze použít smyčky, bloky, if / else příkazy a další řídicí struktury běžné v C#. Jsem omezen na používání výrazů. Za druhé nemohu rekurzivně volat stejný výraz.
Mohl bych, kdyby to byl již delegát, ale nemohu volat ve formě stromu výrazů. V části o [vytváření stromů výrazů](expression-trees-building.md) se naučíte techniky k překonání těchto omezení.

V tomto výrazu narazíte na uzly všech těchto typů:

1. Equal (binární výraz)
2. Násobení (binární výraz)
3. Podmíněné (? : výraz)
4. Výraz volání metody `Range()` `Aggregate()`(volání a )

Jedním ze způsobů, jak upravit algoritmus návštěvníka je, aby jeho provádění `default` a psát typ uzlu pokaždé, když dosáhnete klauzule. Po několika iterací, budete mít viděli každý z potenciálních uzlů. Pak máte vše, co potřebujete. Výsledkem by bylo něco takového:

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

ConditionalVisitor a MethodCallVisitor zpracovat tyto dva uzly:

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

A výstup pro strom výrazby:

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

## <a name="extending-the-sample-library"></a>Rozšíření ukázkové knihovny

Ukázky v této části zobrazit základní techniky k návštěvě a prozkoumání uzly ve stromu výrazů. I glosoval mnoho akcí, které byste mohli potřebovat, aby se soustředit na základní úkoly návštěvy a přístup uzly ve stromu výrazu.

Za prvé, návštěvníci zpracovávají pouze konstanty, které jsou celá čísla. Konstantní hodnoty může být jakýkoli jiný číselný typ a jazyk C# podporuje převody a propagační akce mezi těmito typy. Robustnější verze tohoto kódu by zrcadlit všechny tyto možnosti.

I poslední příklad rozpozná podmnožinu možných typů uzlů.
Stále jej můžete krmit mnoha výrazy, které způsobí, že se nezdaří.
Úplná implementace je zahrnuta v standardu .NET pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a může zpracovat všechny možné typy uzlů.

Konečně, knihovna jsem použil v tomto článku byl postaven pro demonstraci a učení. Není to optimalizované. Napsal jsem to, aby se struktury používané velmi jasné, a upozornit na techniky používané k návštěvě uzly a analyzovat, co tam je. Implementace výroby by věnovala větší pozornost výkonu než já.

I s těmito omezeními byste měli být na dobré cestě k psaní algoritmů, které čtou a rozumí stromům výrazů.

[Další -- Stavební výrazy](expression-trees-building.md)
