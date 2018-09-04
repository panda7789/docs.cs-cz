---
title: Výrazy lambda
description: Další použití lambda výrazů, které jsou bloky spustitelného kódu, které mohou být předány jako argumenty.
ms.author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 2469e8a0fbf8181a720201637ab5ac5ef02055d4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400862"
---
# <a name="lambda-expressions"></a>Výrazy lambda #

A *výraz lambda* je blok kódu (výraz nebo blok příkazů, který), který je zpracováván jako objekt. Může být předán jako argument metody, a to může být vrácen voláním metody. Výrazy lambda jsou často používány pro:

- Předejte kód, který má být proveden na asynchronní metody, jako je <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Zápis [LINQ – výrazy dotazů](linq/index.md).

- Vytváření [stromů výrazů](expression-trees-building.md).

Použití výrazů lambda je kód, který může být reprezentována jako delegát nebo jako strom výrazů, který se zkompiluje do delegáta. Na typ delegáta konkrétní výraz lambda závisí na jeho parametry a vracet hodnotu. Výrazy lambda, které nevracejí hodnotu odpovídají konkrétní `Action` delegovat, v závislosti na jeho počet parametrů. Lambda výrazy, které vracejí hodnotu odpovídají konkrétní `Func` delegovat, v závislosti na jeho počet parametrů. Například výraz lambda, který má dva parametry, ale nevrací žádnou hodnotu odpovídá <xref:System.Action%602> delegovat. Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.

Používá výraz lambda `=>`, [deklarace operátoru lambda](language-reference/operators/lambda-operator.md), seznam parametrů lambda pro oddělení od jeho spustitelného kódu. Pokud chcete vytvořit výraz lambda, zadejte vstupní parametry (pokud existuje) na levé straně operátoru lambda a umístěte blok výrazu nebo příkazu na druhé straně. Například výraz lambda jednořádkového `x => x * x` určuje parametr s názvem `x` a vrátí hodnotu `x` ve čtverci. Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Nebo jej lze předat přímo jako argument metody:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Výrazové lambdy ##

 Výraz lambda s výrazem na pravé straně = > – operátor je volána *výrazu lambda*. Výrazové lambdy se často používají v konstrukci [stromů výrazů](expression-trees.md). Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

```csharp
(input parameters) => expression
```

Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány. Zadejte nulové vstupní parametry s prázdnými závorkami:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Kompilátor používá obvykle odvození typu při určování typy parametrů. Někdy je však obtížné či nemožné odvodit vstupní typy kompilátor. Pokud k tomu dojde, můžete určit typy explicitně, jako v následujícím příkladu:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody. Ale pokud vytváříte stromy výrazů, které jsou vyhodnocovány mimo rozhraní .NET Framework, například systému SQL Server nebo Entity Framework (EF), můžete neměly by pomocí volání metody v lambda výrazech, protože může metody nemají význam mimo kontext implementace .NET. Pokud budete chtít v tomto případě používat volání metody, nezapomeňte otestovat jejich důkladně a zkontrolujte, že metoda, kterou lze úspěšně vyřešit volání.

## <a name="statement-lambdas"></a>Příkazové lambdy ##

Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:

```csharp
(input parameters) => { statement; }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.

## <a name="async-lambdas"></a>Asynchronní lambdy ##

Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](language-reference/keywords/async.md) a [await](language-reference/keywords/await.md) klíčová slova. Například v příkladu volá `ShowSquares` metodu, která se spustí asynchronně.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Výrazy lambda a řazené kolekce členů ##

Od verze C# 7.0, jazyk C# obsahuje integrovanou podporu pro řazené kolekce členů. Řazená kolekce členů můžete zadat jako argument výraz lambda, a výraz lambda může také vrátit řazené kolekce členů. V některých případech kompilátor jazyka C# používá odvození typu k určení typů součásti řazené kolekce členů.

Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam svých komponent do závorek. Následující příklad používá řazené kolekce členů s 5 součásti předat výraz lambda, zdvojnásobí každou hodnotu, která vrací řazenou kolekci členů s 5 komponenty, který obsahuje výsledek součinů sekvenci čísel.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Obvykle jsou pojmenované pole řazená kolekce členů `Item1`, `Item2`atd. Řazená kolekce členů s s názvem komponenty, můžete definovat, stejně jako v následujícím příkladu.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Další informace o podpoře pro řazené kolekce členů v C# najdete v tématu [typy řazené kolekce členů jazyka C#](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Výrazy lambda s operátory standardního dotazu ##

LINQ na objekty v jiných implementacích má vstupní parametr, jehož typ je jednou z <xref:System.Func%601> řady obecných delegátů. Tyto delegáty používají parametry typu pro definování počtu a typu vstupních parametrů a návratový typ delegáta. `Func` Delegáti jsou velmi užiteční pro zapouzdření výrazů definovaných uživatelem, které jsou použity pro každý prvek v sadě zdrojových dat. Představme si třeba, <xref:System.Func%601> delegáta, jehož syntaxe je:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Delegát může být vytvořena s kód podobný tomuto

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

kde `int` je vstupní parametr a `bool` je návratová hodnota. Vrácená hodnota je vždy určena v posledním parametru typu. Když následující `Func` je vyvolán delegát, vrátí hodnotu true nebo false označuje, zda je vstupní parametr roven hodnotě 5:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Výraz lambda lze také zadat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například ve standardních operátorech dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu. Pokud zadáte <xref:System.Linq.Expressions.Expression%601> je argument, výraz lambda kompilována na strom výrazu. V následujícím příkladu [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standardní operátor dotazu.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento konkrétní výraz lambda vrátí ta celá čísla (`n`), která po vydělení dvěma, mají zbytek 1.

Následující příklad vytvoří posloupnost, která obsahuje všechny prvky `numbers` pole, které před 9, protože se jedná o první číslo v sekvenci, která nesplňuje podmínku.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

Následující příklad určuje většího počtu vstupních parametrů uzavřením do závorek. Metoda vrátí všechny prvky v poli čísel, dokud nenarazí na číslo, jehož hodnota je menší než její pořadové umístění v poli.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu proměnné ve výrazech lambda ##

Při psaní výrazů lambda, často není nutné zadat typ pro vstupní parametry, protože kompilátor může odvodit typ na základě hlavní část výrazu lambda, typy parametrů a dalších faktorů, jak je popsáno ve specifikaci jazyka C#. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje `IEnumerable<Customer>`, pak je vstupní proměnná odvozena jako `Customer` objekt, což znamená, že máte přístup k jejím metodám a vlastnostem:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Obecná pravidla pro odvození typu proměnné pro výrazy lambda jsou:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Každá vstupní argument ve výrazu lambda musí být implicitně převeditelný na odpovídající parametr delegátu.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.

Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“. Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda. V těchto případech typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ na který je převeden výraz lambda.

## <a name="variable-scope-in-lambda-expressions"></a>Rozsah proměnné ve výrazech lambda ##

Výrazy lambda mohou odkazovat na *vnější proměnné* (viz [anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metodě, která definuje funkci lambda, nebo v rozsahu typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad znázorňuje tato pravidla.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:

- Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.

- Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.

- Výraz lambda nemůže přímo zachytit `in`, `ref`, nebo `out` parametr z ohraničující metody.

- Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.

- Výraz lambda nemůže obsahovat `goto` příkazu `break` příkazu, nebo `continue` příkaz, který se nachází uvnitř funkce lambda, pokud cíl příkazu skoku je mimo blok. Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.

## <a name="see-also"></a>Viz také: ##

- [LINQ (Language-Integrated Query)](../standard/using-linq.md)
- [Anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Stromy výrazů](expression-trees.md)
