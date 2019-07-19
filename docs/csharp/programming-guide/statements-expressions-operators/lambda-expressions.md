---
title: Výrazy lambda – C# Průvodce programováním
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 786c2937a3f413170665c39464dc2c94417008ad
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331367"
---
# <a name="lambda-expressions-c-programming-guide"></a>Výrazy lambda (C# Průvodce programováním)

*Výraz lambda* je blok kódu (výraz nebo blok příkazu), který je považován za objekt. Může být předán jako argument metodám a může být také vrácen voláním metody. Výrazy lambda se používají rozsáhle pro:

- Předání kódu, který má být proveden na asynchronní metody, například <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.

- Zápis [výrazů dotazů LINQ](../../linq/index.md).

- Vytváření [stromů výrazů](../concepts/expression-trees/index.md).

Lambda výrazy jsou kód, který lze reprezentovat buď jako delegát, nebo jako strom výrazu, který se zkompiluje do delegáta. Konkrétní typ delegáta výrazu lambda závisí na jeho parametrech a návratové hodnotě. Lambda výrazy, které nevracejí hodnotu odpovídají konkrétnímu `Action` delegátu, v závislosti na počtu parametrů. Lambda výrazy, které vracejí hodnotu odpovídají konkrétnímu `Func` delegátu v závislosti na počtu parametrů. Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu, <xref:System.Action%602> odpovídá delegátu. Výraz lambda, který má jeden parametr a vrací hodnotu, odpovídá <xref:System.Func%602> delegátu.

Výraz lambda používá `=>` [operátor deklarace lambda](../../language-reference/operators/lambda-operator.md), který odděluje seznam parametrů lambda ze spustitelného kódu. Chcete-li vytvořit výraz lambda, zadejte vstupní parametry (pokud existují) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhou stranu. Například výraz `x => x * x` lambda s jedním řádkem určuje parametr s názvem `x` `x` a vrátí hodnotu Square. Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Lambda výraz můžete také přiřadit typu stromu výrazu:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Nebo ho můžete předat přímo jako argument metody:

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Použijete-li syntaxi založenou na metodě pro <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> volání metody <xref:System.Linq.Enumerable?displayProperty=nameWithType> ve třídě (stejně jako v LINQ to Objects a LINQ to XML), parametr je typ <xref:System.Func%602?displayProperty=nameWithType>delegáta. Výraz lambda je nejvhodnějším způsobem vytvoření tohoto delegátu. Při volání <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> ve třídě (stejně jako v LINQ to SQL) je typ parametru typ [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)stromu výrazu. Výraz lambda je opět pouze velmi stručným způsobem vytvoření tohoto stromu výrazu. Výrazy lambda umožňují, `Select` aby volání vypadaly podobně, i když ve skutečnosti typ objektu vytvořeného z výrazu lambda je jiný.

Všechna omezení, která platí pro [anonymní metody](anonymous-methods.md) , platí také pro výrazy lambda.
  
## <a name="expression-lambdas"></a>Výrazy lambda výrazu

Výraz lambda s výrazem na pravé straně `=>` operátoru se nazývá výrazová *lambda*. Výrazy lambda výrazů se v konstrukci [stromů výrazů](../concepts/expression-trees/index.md)používají rozsáhle. Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

```csharp
(input-parameters) => expression
```

Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.

Zadejte nulové vstupní parametry s prázdnými závorkami:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

V některých případech je možné, že kompilátor odvodí vstupní typy. Můžete určit typy explicitně, jak je znázorněno v následujícím příkladu:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy vstupních parametrů musí být všechny explicitní nebo všechny implicitní; v opačném případě dojde k chybě kompilátoru [CS0748](../../misc/cs0748.md) .

Tělo výrazu lambda se může skládat z volání metody. Pokud však vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext modulu CLR (Common Language Runtime) .NET, například v SQL Server, neměli byste používat volání metody ve výrazech lambda. Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.

## <a name="statement-lambdas"></a>Výrazy lambda příkazů

Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:

```csharp  
(input-parameters) => { statement; }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.
  
## <a name="async-lambdas"></a>Asynchronní výrazy lambda

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../language-reference/keywords/async.md) a [await](../../language-reference/keywords/await.md) . Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.

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

Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Výrazy lambda a řazené kolekce členů

Od verze C# 7,0 poskytuje C# jazyk integrovanou podporu pro [řazené kolekce členů](../../tuples.md). Můžete zadat řazenou kolekci členů jako argument pro lambda výraz a váš výraz lambda může také vrátit řazenou kolekci členů. V některých případech C# kompilátor používá odvození typu k určení typů komponent řazené kolekce členů.

Řazenou kolekci členů můžete definovat tak, že v závorkách seřadíte seznam jeho komponent oddělených čárkami. Následující příklad používá řazené kolekce členů se třemi komponenty k předání sekvence čísel lambda výrazu, který zdvojnásobuje každou hodnotu a vrátí řazenou kolekci členů se třemi komponentami, které obsahují výsledek násobení.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Obvykle se pole řazené kolekce členů `Item1`nazývají, `Item2`atd. Můžete však definovat řazenou kolekci členů s pojmenovanými součástmi, jak je uvedeno v následujícím příkladu.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Další informace o C# řazených kolekcích členů naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Výrazy lambda se standardními operátory dotazu

LINQ to Objects, mimo jiné implementace, má vstupní parametr, jehož typ je jeden z <xref:System.Func%601> řad generických delegátů. Tito Delegáti používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta. `Func`Delegáti jsou velmi užiteční pro zapouzdření uživatelsky definovaných výrazů, které jsou aplikovány na každý prvek v sadě zdrojových dat. Zvažte například typ <xref:System.Func%602> delegáta:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegát může být vytvořen jako `Func<int, bool>` instance, kde `int` je vstupní parametr a `bool` je návratovou hodnotou. Vrácená hodnota je vždy určena v posledním parametru typu. Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry `string`, `int` a a návratový typ `bool`. Následující `Func` delegát, pokud je vyvolána, vrátí logickou hodnotu, která označuje, zda je vstupní parametr roven pěti:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Výraz lambda lze také zadat <xref:System.Linq.Expressions.Expression%601>, pokud je typ argumentu, například ve standardních operátorech dotazu, které jsou definovány <xref:System.Linq.Queryable> v typu. Při zadání <xref:System.Linq.Expressions.Expression%601> argumentu je výraz lambda zkompilován do stromu výrazu.
  
Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> standardní operátor dotazu:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda počítá tato celá čísla (`n`), která při vydělení dvěma mají zbytek 1.

Následující příklad vytvoří sekvenci, která obsahuje všechny prvky v `numbers` poli, které předcházejí hodnotě 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Následující příklad určuje více vstupních parametrů uzavřením do závorek. Metoda vrátí všechny prvky v `numbers` poli, dokud nenarazí na číslo, jehož hodnota je menší než pořadové místo v poli:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu ve výrazech lambda

Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě těla lambda, typů parametrů a dalších faktorů, jak je popsáno ve specifikaci C# jazyka. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje `IEnumerable<Customer>`na, pak vstupní proměnná je odvozena `Customer` jako objekt, což znamená, že máte přístup ke svým metodám a vlastnostem:  

```csharp
customers.Where(c => c.City == "London");
```

Obecná pravidla pro odvození typu pro výrazy lambda jsou následující:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.
  
Všimněte si, že lambda výrazy samy nemají typ, protože společný typ systému nemá žádný vnitřní koncept výrazu lambda. Někdy je však vhodné mluvit neformálně jako "typ" výrazu lambda. V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ, na který je výraz lambda převeden.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Zachycení vnějších proměnných a rozsahu proměnné ve výrazech lambda

Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](anonymous-methods.md)), které jsou v oboru v metodě definující výraz lambda nebo v rozsahu v typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:  

- Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.

- Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné v nadřazené metodě.

- Výraz lambda nemůže přímo zachytit parametr [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)nebo [out](../../language-reference/keywords/out-parameter-modifier.md) z nadřazené metody.

- Příkaz [return](../../language-reference/keywords/return.md) ve výrazu lambda nezpůsobí vrácení ohraničující metody.

- Výraz lambda nemůže obsahovat příkaz [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)nebo [Continue](../../language-reference/keywords/continue.md) , pokud cíl tohoto příkazu skoku je mimo blok výrazu lambda. Je také možné, že příkaz skoku je mimo blok výrazu lambda, pokud je cíl uvnitř bloku.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>Doporučená kapitola knihy

[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: Více než 250 řešení pro C# 3,0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [LINQ (jazykově integrovaný dotaz)](../concepts/linq/index.md)
- [Anonymní metody](anonymous-methods.md)
- [Stromy výrazů](../concepts/expression-trees/index.md)
- [Místní funkce ve srovnání s lambda výrazy](../../local-functions-vs-lambdas.md)
- [Implicitně typované výrazy lambda](../../implicitly-typed-lambda-expressions.md)
- [Ukázky sady Visual C# Studio 2008 (viz soubory ukázkových dotazů LINQ a program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekurzivní výrazy lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
