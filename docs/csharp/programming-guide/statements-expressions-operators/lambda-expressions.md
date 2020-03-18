---
title: Lambda výrazy - C# Programovací průvodce
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: c549b9fcc91401aed846afd39e656b60e16afb74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937602"
---
# <a name="lambda-expressions-c-programming-guide"></a>Lambda výrazy (C# Programovací průvodce)

*Výraz lambda* je výrazem některé z následujících dvou forem:

- [Výraz lambda,](#expression-lambdas) který má výraz jako jeho tělo:

  ```csharp
  (input-parameters) => expression
  ```

- [Prohlášení lambda,](#statement-lambdas) který má prohlášení blok jako jeho tělo:

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

Pomocí [operátoru `=>` lambda prohlášení](../../language-reference/operators/lambda-operator.md) oddělte seznam parametrů lambda od jeho těla. Chcete-li vytvořit výraz lambda, zadejte vstupní parametry (pokud existují) na levé straně operátoru lambda a výraz nebo blok příkazu na druhé straně.

Libovolný výraz lambda lze převést na typ [delegáta.](../../language-reference/builtin-types/reference-types.md#the-delegate-type) Typ delegáta, na který lze převést výraz lambda, je definován typy jeho parametrů a návratové hodnoty. Pokud výraz lambda nevrátí hodnotu, lze jej převést na `Action` jeden z typů delegáta; v opačném případě jej lze převést na jeden z typů delegáta. `Func` Například lambda výraz, který má dva parametry a vrátí <xref:System.Action%602> žádnou hodnotu lze převést na delegáta. Lambda výraz, který má jeden parametr a vrátí <xref:System.Func%602> hodnotu lze převést na delegáta. V následujícím příkladu je výraz `x => x * x`lambda , který určuje `x` pojmenovaný parametr `x` a vrací hodnotu kvadratických, přiřazen proměnné typu delegáta:

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

Výraz lambdas lze také převést na typy [stromu výrazů,](../concepts/expression-trees/index.md) jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

Výrazy lambda můžete použít v libovolném kódu, který vyžaduje instance typů delegátů <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> nebo stromů výrazů, například jako argument metody pro předání kódu, který by měl být proveden na pozadí. Můžete také použít lambda výrazy při zápisu [LINQ v C#](../../linq/index.md), jak ukazuje následující příklad:

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

Při použití syntaxe založené na <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> metodě <xref:System.Linq.Enumerable?displayProperty=nameWithType> k volání metody ve třídě, například v LINQ to <xref:System.Func%602?displayProperty=nameWithType>Objects a LINQ do XML, parametr je typ delegáta . Při volání <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody ve <xref:System.Linq.Queryable?displayProperty=nameWithType> třídě, například v LINQ na SQL, je [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typem parametru typ stromu výrazu . V obou případech můžete použít stejný výraz lambda k určení hodnoty parametru. To dělá `Select` dvě volání vypadat podobně, i když ve skutečnosti typ objektů vytvořených z lambdas se liší.
  
## <a name="expression-lambdas"></a>Výraz lambdas

Lambda výraz s výrazem na pravé `=>` straně operátoru se nazývá *výraz lambda*. Výraz lambdas se ve velké míře používají při stavbě [stromů výrazů](../concepts/expression-trees/index.md). Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

```csharp
(input-parameters) => expression
```

Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány.

Zadejte nulové vstupní parametry s prázdnými závorkami:  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

Někdy je nemožné pro kompilátor odvodit vstupní typy. Typy můžete zadat explicitně, jak je znázorněno v následujícím příkladu:

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

Typy vstupních parametrů musí být všechny explicitní nebo všechny implicitní; v opačném případě dojde k chybě kompilátoru [CS0748.](../../misc/cs0748.md)

Tělo výrazu lambda se může skládat z volání metody. Pokud však vytváříte stromy výrazů, které jsou vyhodnocovány mimo kontext modulu runtime běžného jazyka .NET, například v serveru SQL Server, neměli byste používat volání metod ve výrazech lambda. Metody nemají význam mimo kontext modulu CLR (Common Language Runtime) rozhraní .NET.

## <a name="statement-lambdas"></a>Prohlášení lambdas

Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

Příkaz lambdas nelze použít k vytvoření stromů výrazů.
  
## <a name="async-lambdas"></a>Asynchronní lambdy

Můžete snadno vytvořit lambda výrazy a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../language-reference/keywords/async.md) a [čekat](../../language-reference/operators/await.md) klíčová slova. Například následující příklad windows forms obsahuje obslužnou rutinu události, `ExampleMethodAsync`která volá a čeká na asynchronní metodu .

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

Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy. Chcete-li přidat tuto `async` obslužnou rutinu, přidejte modifikátor před seznam parametrů lambda, jak ukazuje následující příklad:

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

Další informace o vytváření a používání asynchronních metod naleznete [v tématu Asynchronní programování s asynchronní a await](../concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda výrazy a řazené kolekce členů

Počínaje C# 7.0, jazyk C# poskytuje integrovanou podporu pro [řazené kolekce členů](../../tuples.md). Řazené kolekce členů můžete poskytnout jako argument výrazu lambda a výraz lambda můžete také vrátit řazenou kolekce členů. V některých případech kompilátor Jazyka C# používá odvození typu k určení typů součástí řazené kolekce členů.

Řazená kolekce členů definujete uzavřením seznamu jeho součástí oddělených čárkami do závorek. Následující příklad používá řazenou kolekce členů se třemi součástmi předat posloupnost čísel do výrazu lambda, který zdvojnásobí každou hodnotu a vrátí řazenou skupinu se třemi součástmi, které obsahují výsledek násobení.

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

Pole n-tice jsou obvykle `Item1`pojmenována , `Item2`, atd. Můžete však definovat řazenou kolekce členů s pojmenovanými součástmi, jako to dělá následující příklad.

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

Další informace o kolekcí členů řaděných kolekcí členů jazyka C# naleznete v tématu [C# typy řazené kolekce členů](../../tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas se standardními operátory dotazů

LINQ to Objects, mimo jiné implementace, mají vstupní parametr, jehož typ je jedním z <xref:System.Func%601> rodiny obecných delegátů. Tito delegáti používají parametry typu k definování počtu a typu vstupních parametrů a návratového typu delegáta. `Func`delegáti jsou velmi užitečné pro zapouzdření uživatelem definované výrazy, které jsou použity pro každý prvek v sadě zdrojových dat. Zvažte například <xref:System.Func%602> typ delegáta:  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

Delegát může být vytvořena jako `Func<int, bool>` instance, `int` kde je `bool` vstupní parametr a je vrácená hodnota. Vrácená hodnota je vždy určena v posledním parametru typu. Například `Func<int, string, bool>` definuje delegáta se dvěma `int` vstupními parametry `string`a `bool`, a návratový typ . Následující `Func` delegát, když je vyvolán, vrátí logickou hodnotu, která označuje, zda je vstupní parametr roven pěti:

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

Výraz lambda můžete zadat také v případě, že typ argumentu <xref:System.Linq.Expressions.Expression%601>je , <xref:System.Linq.Queryable> například ve standardních operátorech dotazů, které jsou definovány v typu. Když zadáte <xref:System.Linq.Expressions.Expression%601> argument, lambda je zkompilován do stromu výrazů.
  
Následující příklad používá <xref:System.Linq.Enumerable.Count%2A> standardní operátor dotazu:

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda počítá celá`n`čísla ( ), která při dělení dvěma mají zbytek 1.

Následující příklad vytvoří sekvenci, která `numbers` obsahuje všechny prvky v poli, které předcházejí 9, protože to je první číslo v pořadí, které nesplňuje podmínku:

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

Následující příklad určuje více vstupních parametrů jejich uzavřením do závorek. Metoda vrátí všechny prvky `numbers` v poli, dokud nenarazí na číslo, jehož hodnota je menší než jeho ordinální pozice v poli:

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu ve výrazech lambda

Při psaní lambdas, často není nutné zadat typ pro vstupní parametry, protože kompilátor můžete odvodit typ na základě lambda tělo, typy parametrů a další faktory, jak je popsáno ve specifikaci jazyka C#. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud dotazujete `IEnumerable<Customer>`na , je vstupní proměnná `Customer` odvozena jako objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:  

```csharp
customers.Where(c => c.City == "London");
```

Obecná pravidla pro odvození typu pro lambdy jsou následující:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Každý vstupní parametr ve výrazu lambda musí být implicitně převoditelný na odpovídající parametr delegátu.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.
  
Všimněte si, že lambda výrazy samy o sobě nemají typ, protože společný systém typu nemá žádný vnitřní koncept "lambda výraz." Někdy je však vhodné mluvit neformálně o "typu" výrazu lambda. V těchto případech typ odkazuje na <xref:System.Linq.Expressions.Expression> typ delegáta nebo typ, na který je převeden výraz lambda.

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a>Zachycení vnějších proměnných a rozsahu proměnných ve výrazech lambda

Lambdas může odkazovat na *vnější proměnné*. Jedná se o proměnné, které jsou v oboru v metodě, která definuje výraz lambda nebo v oboru v typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla:

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:  

- Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.

- Proměnné zavedené v rámci výrazu lambda nejsou viditelné v ohraničující metodě.

- Výraz lambda nemůže přímo zachytit parametr [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)nebo [out](../../language-reference/keywords/out-parameter-modifier.md) z ohraničující metody.

- Příkaz [return](../../language-reference/keywords/return.md) ve výrazu lambda nezpůsobí vrácení ohraničující metody.

- Výraz lambda nemůže [obsahovat](../../language-reference/keywords/goto.md)příkaz goto , [break](../../language-reference/keywords/break.md)nebo [continue,](../../language-reference/keywords/continue.md) pokud je cíl tohoto příkazu skok mimo blok výrazu lambda. Je také chyba mít příkaz skok mimo blok výrazu lambda, pokud je cíl uvnitř bloku.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="featured-book-chapter"></a>Nejlepší kapitola knihy

[Delegáti, události a Lambda výrazy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) v [C# 3.0 Kuchařka, Třetí vydání: Více než 250 řešení pro C# 3.0 programátory](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [LINQ (dotaz integrovaný jazykem)](../concepts/linq/index.md)
- [Stromy výrazů](../concepts/expression-trees/index.md)
- [Místní funkce ve srovnání s lambda výrazy](../../local-functions-vs-lambdas.md)
- [Implicitně zadané lambda výrazy](../../implicitly-typed-lambda-expressions.md)
- [Ukázky visual studia 2008 C# (viz soubory ukázkových dotazů LINQ a program XQuery)](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [Rekurzivní lambda výrazy](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
