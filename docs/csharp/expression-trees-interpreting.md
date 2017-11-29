---
title: "Interpretace výrazy"
description: "Zjistěte, jak napsat kód pro zjištění strukturu strom výrazu se nezdařilo."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: e7c5f7404546c6f3812fc5cc3d0320c77816634d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-expressions"></a>Interpretace výrazy

[Předchozí – Provádění výrazy](expression-trees-execution.md)

Teď můžete napsat kód, který zkontrolujte strukturu *strom výrazu*. Každý uzel ve stromu výrazů bude objekt třídy, který je odvozený od `Expression`.

Tento návrh díky návštěvou všechny uzly v operaci relativně splněny následující rekurzivní strom výrazu. Obecné strategie je spuštění na kořenový uzel a zjistit, jaký druh uzlu je.

Pokud má typ uzlu podřízené objekty, navštivte rekurzivně podřízené objekty. V každém uzlu podřízené, opakujte tento postup použít v kořenovém uzlu: určit typ a pokud má typ podřízené objekty, navštivte všechny podřízené objekty.

## <a name="examining-an-expression-with-no-children"></a>Zkoumání výraz s žádné podřízené objekty
Začněme tím, kteří navštěvují každý uzel ve stromu velmi jednoduchý výraz.
Tady je kód, který vytvoří konstantní výraz a poté zkoumá jeho vlastnosti:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

To bude tisknout následující:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Teď můžete napsat kód, který by Zkontrolujte tento výraz a zapsat některé důležité vlastnosti o něm. Tady je tento kód:

## <a name="examining-a-simple-addition-expression"></a>Zkoumání jednoduchý výraz přidání

Začněme s ukázkou přidání z Úvod do této části.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nepoužívám `var` deklarovat tento strom výrazu, protože není možné, protože je implicitně typované na pravé straně přiřazení. Pro lepší vysvětlení hlubšímu, přečtěte si [zde](implicitly-typed-lambda-expressions.md).

Je kořenový uzel `LambdaExpression`. Chcete-li získat kód zajímavé na pravé straně z `=>` operátor, budete muset najít podřízených objektů `LambdaExpression`. Jsme to udělat pomocí všechny výrazy v této části. Nadřazený uzel Pomozte nám najít návratový typ `LambdaExpression`.

Zkontrolujte každý uzel v tomto výrazu, jsme budete potřebovat k rekurzivnímu najdete na počet uzlů. Zde je jednoduchý první implementace:

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

Tato ukázka se vytiskne následující výstup:

```
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

Můžete si všimnout spoustu opakování v ukázce kódu, výše.
Umožňuje vyčistit a vytvořit více obecné výraz uzlu návštěvníka. Která se bude vyžadovat nám zápis rekurzivní algoritmus. Libovolný uzel může být typu, který může mít podřízené objekty.
Každého uzlu, který má podřízených prvků, vyžaduje nám navštivte tyto děti a zjistit, co je tento uzel. Tady je si verzi, která využívá rekurze přejděte operace přidání vyčištěnými:

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

Tento algoritmus je základem algoritmu, který najdete všechny libovolný `LambdaExpression`. Je celá řada díry, který kód byl vytvořen pouze konkrétně hledá velmi malé ukázkové sady možné uzly stromu výrazu, které mohou nastat. Však stále další odlišují od ji vytvoří. (Výchozí velká písmena v `Visitor.CreateFromExpression` metoda vytiskne zprávu ke konzole chyba vyskytne nového typu uzlu. Tímto způsobem, víte, chcete-li přidat nový typ výrazu.)

Když spustíte tohoto návštěvníka na výše uvedeném Přidání výrazu, získáte tento výstup:

```
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

Teď, když jste sestavili obecnější implementace návštěvníka, můžete navštívit a zpracovat více různých typech výrazy.

## <a name="examining-an-addition-expression-with-many-levels"></a>Zkoumání přidání výraz s mnoha úrovně

Pojďme zkuste složitější příklad, ale stále omezit typy uzlů k přidání pouze:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Před spuštěním to na algoritmu návštěvníka, zkuste myšlenku cvičení pracovat se co může být výstup. Nezapomeňte, že `+` operátor je *binární operátor*: musí mít dva podřízené objekty představující operandy vlevo a vpravo. Existuje několik způsobů možné vytvořit stromu, které by mohly být správné:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Můžete zobrazit oddělení do dvě možné odpovědi chcete zvýraznit nejslibnějším. První představuje *právo asociativní* výrazy. Druhý představují *zbývajících asociativní* výrazy.
Obě tyto dva formáty výhodou je, že formát lze škálovat na libovolný libovolný počet přidání výrazy. 

Pokud spustíte tento výraz prostřednictvím návštěvníka, zobrazí se tato tento výstup ověření, že je výraz jednoduchého přidání *zbývajících asociativní*. 

Aby bylo možné tuto ukázku spustit a najdete v části stromu úplné výrazu, musel jsem jeden změnu provést na strom výrazu zdroje. Když strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnota `10`. Kompilátor provede všechny přidání a snižuje výraz, který má své nejjednodušší podobě. Zobrazíte stromu původní stačí jednoduše přidáním jednu proměnnou ve výrazu:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Vytvořte pro tento součet návštěvníka a spustit návštěvníka uvidíte tento výstup:

```
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

Můžete také spustit žádné z ostatních vzorků prostřednictvím kódu návštěvníka a najdete v části stromu, co představuje. Tady je příklad `sum3` výraz výše (s dalším parametrem zabránit computing konstanta kompilátor):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Toto je výstup z návštěvníka:

```
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

Všimněte si, že závorkách nejsou součástí výstupu. Nejsou žádné uzly strom výrazu, které představují závorkách v vstupní výraz. Struktura stromu výraz obsahuje všechny informace potřebné pro komunikaci prioritu.

## <a name="extending-from-this-sample"></a>Rozšíření od této ukázky

Ukázka se zabývá jenom nejvíce elementární stromů výrazů. Kód, který jste viděli v této části zpracovává pouze konstantní celá čísla a binárního souboru `+` operátor. Jako poslední vzorek můžeme aktualizovat návštěvníka pro zpracování složitějších výraz. Pojďme aby fungoval pro toto:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Tento kód představuje jeden možné implementace matematickém *faktoriál* funkce. Způsob, jak tento kód jsme nenapsali označuje dvě limitiations vytváření stromů výrazů přiřazením výrazy lambda výrazy. Nejprve lambda nejsou povoleny. To znamená, nelze použít smyčky, bloky, pokud / else – příkazy a další ovládací struktury běžné v jazyce C#. Jsem omezeno na použití výrazy. Druhý nelze rekurzivní volání stejný výraz.
Může I pokud již byly delegáta, ale nelze volat v jeho výrazu stromu formuláře. V tomto článku v [vytváření stromů výrazů](expression-trees-building.md) dozvíte techniky k překonat tato omezení.


V tomto výrazu narazíte uzly těchto typů:
1. Rovná (binárního výrazu)
2. Násobení (binárního výrazu)
3. Podmíněné (na? : výraz)
4. Metoda volání výrazu (volání `Range()` a `Aggregate()`)

Jeden způsob, jak upravit algoritmus návštěvníka je zachovat, její provedení a zapisovat typ uzlu pokaždé, když se dostanete vaší `default` klauzule. Po několika iterací budete viděli jste, každý z potenciální uzlů. Potom budete mít vše, které potřebujete. Výsledkem bude přibližně takto:

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

ConditionalVisitor a MethodCallVisitor procesu tyto dva uzly:

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

A by výstup pro strom výrazu:

```
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

## <a name="extending-the-sample-library"></a>Rozšíření knihovny ukázka

Ukázky v této části ukazují základní techniky navštivte a zkontrolujte uzly ve stromu výrazů. I glossed přes mnoho akce, které může být nutné, aby bylo možné soustředit se jenom na klíčové úlohy návštěvou a přístup k uzlům v strom výrazu se nezdařilo. 

Nejprve návštěvníkům zpracovat pouze konstanty, které jsou celá čísla. Konstantní hodnoty může být jiné číselného typu a jazyka C# podporuje převody a reklamními nabídkami mezi tyto typy. Robustnější verzi tento kód by zrcadlení všechny tyto možnosti.

V posledním příkladu rozpozná podmnožinu typy uzlu.
Vám může stále informačního kanálu je mnoho výrazů, které způsobí, že k selhání.
Úplnou implementaci je zahrnuta v rozhraní .NET standardní pod názvem [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) a dokáže zpracovat všechny typy uzlu.

Knihovna, kterou lze použít v tomto článku se nakonec bylo vytvořeno pro demonstrační a učit se. Není optimalizována ho. I napsali, abyste se struktury používá velmi jasně a abyste měli na očích technik navštívit uzly a analýza, co je k dispozici. Provozní implementace by více zaměřit na výkon než je nutné.

I když tyto omezení musí být i na moct zápis algoritmy, které pro čtení a pochopení stromů výrazů.

[Další--Vytváření výrazy](expression-trees-building.md)
