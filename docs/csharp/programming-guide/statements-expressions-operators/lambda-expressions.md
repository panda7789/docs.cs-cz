---
title: Výrazy lambda – C# Průvodce programováním
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 668bb08526a6eeb1cf640c9ecdac3b8f2c850a99
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711945"
---
# <a name="lambda-expressions-c-programming-guide"></a>Výrazy lambda (C# Průvodce programováním)

*Výraz lambda* je výraz kterékoli z následujících dvou forem:

- [Výraz lambda výrazu](#expression-lambdas) , který má výraz jako tělo:

  ```csharp
  (input-parameters) => expression
  ```

- Výraz [lambda](#statement-lambdas) , který má blok příkazu jako jeho tělo:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Použijte [operátor deklarace lambda `=>`](../../language-reference/operators/lambda-operator.md) k oddělení seznamu parametrů lambda od jeho těla. Chcete-li vytvořit výraz lambda, zadejte vstupní parametry (pokud existují) na levé straně operátoru lambda a výraz nebo blok příkazu na druhé straně.

Libovolný výraz lambda lze převést na typ [delegáta](../../language-reference/builtin-types/reference-types.md#the-delegate-type) . Typ delegáta, na který lze výraz lambda převést, je definován typy jeho parametrů a návratové hodnoty. Pokud výraz lambda nevrací hodnotu, může být převeden na jeden z `Action`ch typů delegátů; v opačném případě je možné ji převést na jeden z `Func` typů delegátů. Například lambda výraz, který má dva parametry a nevrací žádnou hodnotu, lze převést na <xref:System.Action%602> delegáta. Lambda výraz, který má jeden parametr a vrací hodnotu, lze převést na <xref:System.Func%602> delegáta. V následujícím příkladu výraz lambda `x => x * x`, který určuje parametr s názvem `x` a vrátí hodnotu `x` na druhou, je přiřazen proměnné typu delegáta:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Lambda výrazy lze také převést na typy [stromu výrazů](../concepts/expression-trees/index.md) , jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Můžete použít výrazy lambda v jakémkoli kódu, který vyžaduje instance typů delegátů nebo stromů výrazů, například jako argument metody <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> k předání kódu, který by měl být proveden na pozadí. Lambda výrazy můžete použít také při psaní [LINQ in C# ](../../linq/index.md), jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Použijete-li syntaxi na základě metody pro volání metody <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> ve třídě <xref:System.Linq.Enumerable?displayProperty=nameWithType>, například v LINQ to Objects a LINQ to XML, je parametrem typ delegáta <xref:System.Func%602?displayProperty=nameWithType>. Při volání metody <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> ve třídě <xref:System.Linq.Queryable?displayProperty=nameWithType>, například v LINQ to SQL, je typ parametru typ stromu výrazu [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>). V obou případech můžete použít stejný výraz lambda k zadání hodnoty parametru. To umožňuje, aby dvě `Select` volání vypadaly podobně, i když ve skutečnosti se typ objektů vytvořených z výrazů lambda liší.
  
## <a name="expression-lambdas"></a>Výrazy lambda výrazu

Výraz lambda s výrazem na pravé straně operátoru `=>` se nazývá *výrazová lambda*. Výrazy lambda výrazů se v konstrukci [stromů výrazů](../concepts/expression-trees/index.md)používají rozsáhle. Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

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
(input-parameters) => { <sequence-of-statements> }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Výrazy lambda příkazu nejde použít k vytváření stromů výrazů.
  
## <a name="async-lambdas"></a>Asynchronní výrazy lambda

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../language-reference/keywords/async.md) a [await](../../language-reference/operators/await.md) . Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.

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

Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy. Chcete-li přidat tuto obslužnou rutinu, přidejte modifikátor `async` před seznam parametrů lambda, jak ukazuje následující příklad:

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

Pole řazené kolekce členů jsou obvykle pojmenovány `Item1`, `Item2`atd. Můžete však definovat řazenou kolekci členů s pojmenovanými součástmi, jak je uvedeno v následujícím příkladu.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Další informace o C# řazených kolekcích členů naleznete v tématu [ C# typy řazené kolekce členů](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Výrazy lambda se standardními operátory dotazu

LINQ to Objects, kromě jiných implementací, mají vstupní parametr, jehož typ je jedna z <xref:System.Func%601> rodina generických delegátů. Tito Delegáti používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta. Delegáti `Func` jsou velmi užitečné pro zapouzdření uživatelsky definovaných výrazů, které jsou aplikovány na každý prvek v sadě zdrojových dat. Zvažte například <xref:System.Func%602> typ delegáta:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegát může být vytvořen jako instance `Func<int, bool>`, kde `int` je vstupním parametrem a `bool` je návratovou hodnotou. Vrácená hodnota je vždy určena v posledním parametru typu. Například `Func<int, string, bool>` definuje delegáta se dvěma vstupními parametry, `int` a `string`a návratový typ `bool`. Následující `Func` delegát po jeho vyvolání vrátí logickou hodnotu, která označuje, zda je vstupní parametr roven pěti:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v typu <xref:System.Linq.Queryable>. Při zadání argumentu <xref:System.Linq.Expressions.Expression%601> je výraz lambda zkompilován do stromu výrazu.
  
Následující příklad používá operátor dotazu <xref:System.Linq.Enumerable.Count%2A> Standard:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda počítá tato celá čísla (`n`), která při vydělení dvěma mají zbytek 1.

Následující příklad vytvoří sekvenci, která obsahuje všechny prvky v poli `numbers`, které předcházejí hodnotě 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Následující příklad určuje více vstupních parametrů uzavřením do závorek. Metoda vrátí všechny prvky v poli `numbers`, dokud nenalezne číslo, jehož hodnota je menší než pořadové místo v poli:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu ve výrazech lambda

Při psaní výrazů lambda není často nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě těla lambda, typů parametrů a dalších faktorů, jak je popsáno ve specifikaci C# jazyka. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje na `IEnumerable<Customer>`, vstupní proměnná je odvozená jako `Customer` objekt, což znamená, že máte přístup ke svým metodám a vlastnostem:  

```csharp
customers.Where(c => c.City == "London");
```

Obecná pravidla pro odvození typu pro výrazy lambda jsou následující:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.
  
Všimněte si, že lambda výrazy samy nemají typ, protože společný typ systému nemá žádný vnitřní koncept výrazu lambda. Někdy je však vhodné mluvit neformálně jako "typ" výrazu lambda. V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ, na který je výraz lambda převeden.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Zachycení vnějších proměnných a rozsahu proměnné ve výrazech lambda

Výrazy lambda mohou odkazovat na *vnější proměnné*. Toto jsou proměnné, které jsou v oboru v metodě definující výraz lambda nebo v rozsahu typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla:

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

[Delegáti, události a výrazy lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [ C# 3,0 kuchařka, třetí vydání: více než 250 řešení pro C# 3,0 programátorů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [LINQ (jazykově integrovaný dotaz)](../concepts/linq/index.md)
- [Stromy výrazů](../concepts/expression-trees/index.md)
- [Místní funkce ve srovnání s lambda výrazy](../../local-functions-vs-lambdas.md)
- [Implicitně typované výrazy lambda](../../implicitly-typed-lambda-expressions.md)
- [Ukázky sady Visual C# Studio 2008 (viz soubory ukázkových dotazů LINQ a program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekurzivní výrazy lambda](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
