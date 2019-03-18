---
title: Výrazy lambda - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125730"
---
# <a name="lambda-expressions-c-programming-guide"></a>Výrazy lambda (C# Programming Guide)

A *výraz lambda* je blok kódu (výraz nebo blok příkazů, který), který je zpracováván jako objekt. Může být předán jako argument metody, a to může být vrácen voláním metody. Výrazy lambda jsou často používány pro:

- Předejte kód, který má být proveden na asynchronní metody, jako je <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.

- Zápis [LINQ – výrazy dotazů](../../linq/index.md).

- Vytváření [stromů výrazů](../concepts/expression-trees/index.md).

Použití výrazů lambda je kód, který může být reprezentována jako delegát nebo jako strom výrazů, který se zkompiluje do delegáta. Na typ delegáta konkrétní výraz lambda závisí na jeho parametry a vracet hodnotu. Výrazy lambda, které nevracejí hodnotu odpovídají konkrétní `Action` delegovat, v závislosti na jeho počet parametrů. Lambda výrazy, které vracejí hodnotu odpovídají konkrétní `Func` delegovat, v závislosti na jeho počet parametrů. Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu odpovídá <xref:System.Action%602> delegovat. Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.

Používá výraz lambda `=>`, [deklarace operátoru lambda](../../language-reference/operators/lambda-operator.md), seznam parametrů lambda pro oddělení od jeho spustitelného kódu. Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhé straně. Například výraz lambda jednořádkového `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci. Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Výraz lambda také můžete přiřadit k typu stromu výrazu:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Nebo jej lze předat přímo jako argument metody:

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Při použití syntaxe založených na volání metody na volání <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> metodu <xref:System.Linq.Enumerable?displayProperty=nameWithType> třídy (stejně jako v LINQ na objekty a LINQ to XML) je parametr typu delegáta <xref:System.Func%602?displayProperty=nameWithType>. Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu. Při volání <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metoda ve <xref:System.Linq.Queryable?displayProperty=nameWithType> třídy (stejně jako v technologii LINQ to SQL) je typ parametru typu stromu výrazu [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>). Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu. Výrazy lambda umožňují `Select` volání vypadalo podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda jiný.

Všechna omezení, které se vztahují [anonymní metody](anonymous-methods.md) platí také pro výrazy lambda.
  
## <a name="expression-lambdas"></a>Výrazové lambdy

Výraz lambda s výrazem na pravé straně `=>` operátor je volána *výrazu lambda*. Výrazové lambdy se často používají v konstrukci [stromů výrazů](../concepts/expression-trees/index.md). Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

```csharp
(input-parameters) => expression
```

Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.

Zadejte nulové vstupní parametry s prázdnými závorkami:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Někdy je pro kompilátor odvodit vstupní typy. Můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Vstupní parametr typy musí být všechny explicitní, nebo všechny implicitní; v opačném případě [CS0748](../../misc/cs0748.md) dojde k chybě kompilátoru.

Tělo výrazu lambda se může skládat z volání metody. Ale pokud vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext .NET common language runtime, například v systému SQL Server, byste neměli používat volání metody ve výrazech lambda. Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.

## <a name="statement-lambdas"></a>Příkazové lambdy

Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:

```csharp  
(input-parameters) => { statement; }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.
  
## <a name="async-lambdas"></a>Asynchronní lambdy

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../language-reference/keywords/async.md) a [await](../../language-reference/keywords/await.md) klíčová slova. Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy. Chcete-li přidat tuto obslužnou rutinu, přidejte `async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad:

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Výrazy lambda a řazené kolekce členů

Počínaje C# 7.0, C# jazyk poskytuje integrovanou podporu pro [řazených kolekcí členů](../../tuples.md). Řazená kolekce členů můžete zadat jako argument výraz lambda, a výraz lambda může také vrátit řazené kolekce členů. V některých případech kompilátor jazyka C# používá odvození typu k určení typů součásti řazené kolekce členů.

Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam svých komponent do závorek. Následující příklad používá řazené kolekce členů s tři komponenty předat výraz lambda, zdvojnásobí každou hodnotu, která vrací řazenou kolekci členů s tři komponenty, který obsahuje výsledek součinů sekvenci čísel.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Obvykle jsou pojmenované pole řazená kolekce členů `Item1`, `Item2`atd. Řazená kolekce členů s s názvem komponenty, můžete definovat, stejně jako v následujícím příkladu.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Další informace o C# řazených kolekcí členů, naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Výrazy lambda s operátory standardního dotazu

LINQ na objekty v jiných implementacích má vstupní parametr, jehož typ je jednou z <xref:System.Func%601> řady obecných delegátů. Tyto delegáty používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta. `Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat. Představme si třeba, <xref:System.Func%602> typ delegáta:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegát může být vytvořen jako `Func<int, bool>` instance where `int` je vstupní parametr a `bool` je návratová hodnota. Vrácená hodnota je vždy určena v posledním parametru typu. Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`. Následující `Func` delegáta, při jejím vyvolání a vrátí logickou hodnotu označující, zda je vstupní parametr roven pěti:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu. Pokud zadáte <xref:System.Linq.Expressions.Expression%601> je argument, výraz lambda kompilována na strom výrazu.
  
V následujícím příkladu <xref:System.Linq.Enumerable.Count%2A> standardní operátor dotazu:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda vrátí ta celá čísla (`n`) která po vydělení dvěma mají zbytek 1.

Následující příklad vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které před 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Následující příklad určuje většího počtu vstupních parametrů uzavřením do závorek. Metoda vrátí všechny prvky `numbers` pole, dokud nenarazí na číslo, jehož hodnota je menší než její pořadové umístění v poli:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu proměnné ve výrazech lambda

Při psaní výrazů lambda, často není nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní část výrazu lambda, typy parametrů a dalších faktorů, jak je popsáno v C# specifikace jazyka. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:  

```csharp
customers.Where(c => c.City == "London");
```

Obecná pravidla pro odvození typu proměnné pro výrazy lambda jsou následující:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.
  
Všimněte si, že výrazy lambda nemají typ, protože má obecný systém typů nezná vnitřní pojem "výraz lambda". Někdy je však vhodné hovořit neformálně o "typu" výrazu lambda. V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Rozsah proměnné ve výrazech lambda

Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](anonymous-methods.md)), které jsou v oboru v metodě, která definuje výraz lambda nebo v rozsahu typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:  

- Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.

- Proměnné, které jsou představeny v rámci výrazu lambda nejsou viditelné v ohraničující metody.

- Výraz lambda nemůže přímo zachytit [v](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), nebo [si](../../language-reference/keywords/out-parameter-modifier.md) parametr z ohraničující metody.

- A [vrátit](../../language-reference/keywords/return.md) příkaz ve výrazu lambda nezpůsobí vrácení ohraničující metody.

- Výraz lambda nemůže obsahovat [goto](../../language-reference/keywords/goto.md), [přerušení](../../language-reference/keywords/break.md), nebo [pokračovat](../../language-reference/keywords/continue.md) příkaz, pokud cíl, který příkaz skoku je mimo blok výrazu lambda. Je také chybou mít příkaz skoku mimo blok výrazu lambda, pokud je cíl uvnitř bloku.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>Doporučená kapitola knihy

[Delegáty, události a výrazy Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3.0 Cookbook, Third Edition: Víc než 250 řešení pro C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [LINQ (Language-Integrated Query)](../concepts/linq/index.md)
- [Anonymní metody](anonymous-methods.md)
- [Stromy výrazů](../concepts/expression-trees/index.md)
- [Lokální funkce ve srovnání s výrazy lambda](../../local-functions-vs-lambdas.md)
- [Implicitně typovaná lambda výrazy](../../implicitly-typed-lambda-expressions.md)
- [Visual Studio 2008 C# – ukázky (viz ukázkové soubory dotazů LINQ a XQuery program)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekurzivní výrazy lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
