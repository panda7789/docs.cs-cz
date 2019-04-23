---
title: Interpretace výrazů
description: Zjistěte, jak napsat kód, který zkontrolujte strukturu stromu výrazů.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 952a1c553e2392ffc717dc344dfe77a11f025cc4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211241"
---
# <a name="interpreting-expressions"></a>Interpretace výrazů

[Předchozí – Provádění výrazů](expression-trees-execution.md)

Nyní napíšeme nějaký kód ke kontrole struktury *stromu výrazů*. Každý uzel ve stromu výrazů bude objekt, který je odvozen od třídy `Expression`.

Tento návrh díky navštívit všech uzlů ve stromu výrazu relativně přímo dopředné rekurzivní operace. Ke spuštění v kořenovém uzlu a zjistit, jaký druh uzlu je je obecná strategie.

Pokud má typ uzlu podřízené položky, navštivte rekurzivně podřízené objekty. V každém uzlu podřízené zopakovat tento proces používá v kořenovém uzlu: určení typu a pokud má typ podřízené položky, navštivte každou podřízenou položku.

## <a name="examining-an-expression-with-no-children"></a>Zkoumání výraz s žádné podřízené položky
Začněme tím, že navštívit každý uzel ve stromu výrazu velmi jednoduché.
Tady je kód, který vytvoří konstantní výraz a poté zkoumá jeho vlastnosti:

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

Tím se vytisknou následující:

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

Nyní napíšeme kód, který by prozkoumat tento výraz a vypsat některé důležité vlastnosti o něm. Zde je, že kód:

## <a name="examining-a-simple-addition-expression"></a>Prozkoumání jednoduchého Přidání výrazu

Začněme s ukázkou přidání z úvodu k této sekci.

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> Nepoužívám `var` deklarovat tento strom výrazu, protože není možné protože pravá strana přiřazení je implicitně typované. Pro lepší vysvětlení hlouběji, přečtěte si [tady](implicitly-typed-lambda-expressions.md).

Je kořenový uzel `LambdaExpression`. Pokud chcete získat kód zajímavé na pravé straně výrazu `=>` operátoru, je potřeba najít jeden z podřízených položek `LambdaExpression`. Můžeme to udělat pomocí všechny výrazy v této části. Nadřazený uzel pomohl nám pomohly s nalezením návratového typu `LambdaExpression`.

Prozkoumat každý uzel v tomto výrazu, budeme potřebovat k rekurzivnímu navštěvovat počet uzlů. Tady je jednoduchý první implementace:

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

Tato ukázka zobrazí následující výstup:

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

Můžete si všimnout velké množství opakování v ukázkovém kódu výše.
Pojďme, který vyčistit a sestavit další obecné účely výraz uzlu návštěvníka. Který se bude vyžadovat nám napsat rekurzivní algoritmus. Libovolný uzel může být typu, který může mít podřízené objekty.
Libovolný uzel, který má podřízené položky vyžaduje, abychom navštivte tyto podřízené objekty a zjistit, co je tento uzel. Tady je verze, která využívá rekurze pro návštěvu operace sčítání vyčištěnou:

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

Tento algoritmus je základem algoritmus, který získáte všechny libovolného `LambdaExpression`. Existuje mnoho děr, konkrétně bude vypadat kód jsem vytvořil jenom velmi malé ukázku možné sad uzlů stromu výrazu, které mohou nastat. Ale taky další odlišují od ji vytvoří. (Výchozí případ `Visitor.CreateFromExpression` metoda vytiskne zprávu do konzoly chyba vyskytne nového typu uzlu. Díky tomu víte, chcete-li přidat nový typ výrazu.)

Když spustíte tohoto návštěvníka na přidání výrazu je znázorněno výše, získáte následující výstup:

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

Teď, když jste vytvořili více obecnou implementaci návštěvníka, můžete navštívit a zpracovávat více různé typy výrazů.

## <a name="examining-an-addition-expression-with-many-levels"></a>Zkoumání Přidání výrazu s několika úrovněmi

Teď zkuste složitější příklad, ale stále omezit na přidání pouze typy uzlů:

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

Předtím, než spustíte to na algoritmu návštěvníka, zkuste cvičení promyslet tak co může být výstup. Nezapomeňte, že `+` operátor je *binární operátor*: musí mít dva podřízené prvky představující operandy vlevo a vpravo. Vytvoření stromu, který by mohl být správné několika možné způsoby:

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

Zobrazí se oddělení do dva možné odpovědi, zvýrazněte nejvíce příslibů. První představuje *asociativní zprava* výrazy. Druhý představují *asociativní zleva* výrazy.
Obě tyto dva formáty výhodou je, formát škáluje, aby libovolný libovolný počet výrazů sčítání. 

Při spuštění tohoto výrazu prostřednictvím návštěvníka, zobrazí se tím tento výstup, ověření, je přidání jednoduchého výrazu *asociativní zleva*. 

Pokud chcete tuto ukázku spustit a viděli stromu úplného výrazu, můžu museli měnit jeden na strom výrazu zdroje. Strom výrazu obsahuje všechny konstanty, výsledný strom jednoduše obsahuje konstantní hodnotu `10`. Kompilátor provádí všechna sčítání a snižuje výraz, který má své nejjednodušší podobě. Zobrazíte stromu původní stačí jednoduše přidat jednu proměnnou ve výrazu:

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

Vytvořte pro tento součet návštěvník a spusťte návštěvníka, který se zobrazí tento výstup:

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

Můžete také spustit některý z ostatních vzorků návštěvníka kód a zobrazit stromu, které představuje. Tady je příklad `sum3` výraz výše (s dalším parametrem pro zabránění kompilátoru computingu konstanty):

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

Zde se nachází výstup z návštěvníka:

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

Všimněte si, že závorky nejsou součástí výstupu. Nejsou žádné uzly ve stromu výrazů, které představují závorky v vstupní výraz. Struktura stromu výrazů obsahuje všechny informace potřebné ke komunikaci prioritu.

## <a name="extending-from-this-sample"></a>Rozšíření od této ukázky

Ukázka se zabývá pouze nejvíce základní stromy výrazů. Kód v této části jste viděli pouze zpracovává konstantních celých čísel a binární soubor `+` operátor. Jako ukázku poslední můžeme aktualizovat návštěvníka pro zpracování složitějších výrazů. Můžeme nechat pracovat pro toto:

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

Tento kód představuje jednu možnou implementaci matematické *faktoriál* funkce. Způsob, jakým napsali tento kód ukazuje dvě omezení vytváření stromů výrazů přiřazením výrazy lambda výrazy. Nejprve lambda nejsou povoleny. To znamená nejde mi využít smyčky, bloky, pokud / else příkazy a další ovládací prvek struktury, které jsou běžné v jazyce C#. Já jsem můžete používat výrazy. Za druhé nelze rekurzivní volání stejného výrazu.
Uvidím, pokud již byly delegáta, ale nelze volat v podobě stromu výrazu. V části o [vytváření stromů výrazů](expression-trees-building.md) dozvíte techniky k překonání těchto omezení.

V tomto výrazu narazíte uzly z těchto typů:
1. Stejné (binární výraz)
2. Násobení (binární výraz)
3. Podmíněný ()? : výraz)
4. Metoda volání výrazu (volání `Range()` a `Aggregate()`)

Jedním způsobem, jak upravit návštěvníka algoritmus je zachovat, ale jeho spuštění, a zapisovat typ uzlu pokaždé, když dostanete vaše `default` klauzuli. Po několika iteracích budete mít víte, každý potenciální uzlů. Pak máte všechno, co potřebujete. Výsledek bude vypadat přibližně takto:

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

A bude výstup do stromu výrazů:

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

## <a name="extending-the-sample-library"></a>Rozšíření ukázky knihovny

Příklady v této části ukazují techniky core najdete a uzlů ve stromu výrazů zkoumat. Můžu glossed přes mnoho akcí, které je třeba, abyste se mohli soustředit na základní úkoly návštěv a přístup k uzly ve stromu výrazu. 

Nejprve návštěvníkům zpracovat pouze konstanty, které jsou celá čísla. Konstantní hodnoty, může být libovolného číselného typu a jazyka C# podporuje převody a propagační akce mezi těmito typy. Robustnější verze tohoto kódu bude zrcadlit všechny tyto možnosti.

V poslední příkladu rozpozná podmnožinu typů možného uzlu.
Vám může stále informačního kanálu je mnoho výrazů, které způsobí, že selhala.
Celé provedení je zahrnuto v .NET Standard pod názvem <xref:System.Linq.Expressions.ExpressionVisitor> a dokáže pojmout všechny typy možného uzlu.

A konečně byla vytvořena knihovna, kterou jsem používal v tomto článku pro ukázkové a výukové. Není optimalizována. Napsal jsem ho tak, aby struktury používá jasný a abyste měli na očích techniky najdete uzly a analýzu, co je. Provozní implementace by platit další pozornost k výkonu, než budu mít.

I s těmito omezeními měli byste být na dobré cestě k psaní algoritmy, které čtou a vysvětlení stromů výrazů.

[Další--Sestavení výrazy](expression-trees-building.md)
