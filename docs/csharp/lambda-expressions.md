---
title: "Výrazy lambda"
description: "Principy štíhlého vývoje pro použití výrazů lambda, které jsou bloky spustitelného kódu, které lze předat jako argumenty."
keywords: "Rozhraní .NET, .NET core, výrazů lambda, lambdas, delegáti"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 1a97d830c675c8e3980eddae78f3face279ec6dc
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="lambda-expressions"></a>Lambda – výrazy #

A *výrazu lambda* je blok kódu (výraz nebo příkaz blok), který je považován za objekt. Mohla být předána jako argument pro metody a může vracet také pomocí volání metody. Lambda – výrazy jsou používány pro:

- Předávání kód, který se má provádět na asynchronní metody, jako například <xref:System.Threading.Tasks.Task.Run(System.Action)>.

- Zápis [LINQ – výrazy dotazů](linq/index.md).

- Vytváření [stromů výrazů](expression-trees-building.md).

Lambda – výrazy jsou kód, který může být reprezentován jako delegáta, nebo jako strom výrazu kompilovaný s delegátem. Delegát konkrétní typ výrazu lambda závisí na jeho parametry a vrátí hodnotu. Výrazy lambda, které nevrací hodnotu odpovídají na konkrétní `Action` delegovat, v závislosti na jeho počet parametrů. Výrazy lambda, která vrátí hodnotu odpovídají na konkrétní `Func` delegovat, v závislosti na jeho počet parametrů. Například odpovídá výrazu lambda, která má dva parametry, ale nevrací žádnou hodnotu <xref:System.Action%602> delegovat. Výraz lambda, který má jeden parametr a vrátí hodnotu odpovídá <xref:System.Func%602> delegovat.

Výraz lambda používá `=>`, [lambda deklarace operátor](language-reference/operators/lambda-operator.md), oddělte lambda seznam parametrů z jeho spustitelného kódu. K vytvoření výrazu lambda, zadáte vstupních parametrů (pokud existuje) na levé straně operátoru lambda, a umístí výraz nebo příkaz bloku na druhé straně. Například výrazu lambda jeden řádek `x => x * x` určuje parametr, který je pojmenován `x` a vrátí hodnotu `x` kvadratických. Tento výraz můžete přiřadit typu delegátu, jak ukazuje následující příklad:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

Nebo můžete předat přímo jako argument metody:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a>Lambda výrazy ##

 Výraz lambda s výrazu na pravé straně = > operátor je volána *výrazu lambda*. Lambda výrazy jsou používány při sestavování [stromů výrazů](expression-trees.md). Výrazová lambda vrátí výsledek výrazu a má následující základní podobu:

```csharp
(input parameters) => expression
```

Závorky jsou nepovinné pouze v případě, že lambda má jeden vstupní parametr; v opačném případě jsou vyžadovány. Zadejte nulové vstupní parametry s prázdnými závorkami:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

Dva nebo více vstupních parametrů je odděleno čárkami, které jsou uvedeny v závorkách:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

Normálně kompilátor použije odvození typu při určování typy parametrů. V některých případech je však obtížné nebo dokonce znemožňují kompilátor pro odvození vstupní typy. V takovém případě můžete určit typy explicitně, jako v následujícím příkladu:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

V předchozím příkladu si všimněte, že hlavní část výrazové lambdy může být tvořena voláním metody. Ale při vytváření stromů výrazů, které se vyhodnocují mimo rozhraní .NET Framework, jako třeba v systému SQL Server nebo Entity Framework (EF), můžete neměly by pomocí volání metody v výrazy lambda, protože metody může mít žádný význam mimo kontext implementace rozhraní .NET. Pokud vyberete v takovém případě použijte volání metod, nezapomeňte otestovat důkladně lze zajistit, aby se můžete úspěšně vyřešit volání metody.

## <a name="statement-lambdas"></a>Lambdas – příkaz ##

Příkazová lambda se podobá výrazové lambdě s tím rozdílem, že výrazy jsou uzavřeny ve složených závorkách:

```csharp
(input parameters) => { statement; }
```

Text příkazové lambdy může obsahovat libovolný počet příkazů. V praxi jich však není obvykle více než dva nebo tři.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

Příkazové lambdy nelze stejně jako anonymní metody používat k vytvoření stromů výrazu.

## <a name="async-lambdas"></a>Asynchronní lambdas ##

Můžete snadno vytvořit lambda – výrazy a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](language-reference/keywords/async.md) a [await](language-reference/keywords/await.md) klíčová slova. Například v příkladu volá `ShowSquares` metoda, která spustí asynchronně.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

Další informace o tom, jak vytvořit a použít asynchronní metody najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](programming-guide/concepts/async/index.md).

## <a name="lambda-expressions-and-tuples"></a>Lambda – výrazy a řazených kolekcí členů ##

Od verze 7.0 C#, jazyka C# poskytuje integrovanou podporu pro řazené kolekce členů. Můžete zadat jako argument výraz lambda řazené kolekce členů a vaše výrazu lambda může také vrátit řazené kolekce členů. V některých případech kompilátor jazyka C# pomocí odvození typu Určuje typy součástí řazené kolekce členů. 

Můžete definovat řazené kolekce členů uzavřením čárkami oddělený seznam jeho součástí do závorek. Následující příklad používá řazené kolekce členů s 5 součásti předat výrazu lambda, která zdvojnásobí každou hodnotu a vrátí řazené kolekce členů s 5 komponenty obsahující výsledek součinů pořadí čísel.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

Obvykle jsou pojmenované pole řazené kolekce členů `Item1`, `Item2`atd. Můžete však definovat řazené kolekce členů s s názvem součásti, stejně jako v následujícím příkladu.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

Další informace o podpoře pro řazené kolekce členů v jazyce C#, najdete v části [typy C# řazené kolekce členů](tuples.md).

## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas s standardní operátory dotazu ##

LINQ na objekty mezi jiných implementacích mít vstupní parametr s typem je jedním z <xref:System.Func%601> rodiny obecných delegátů. Tyto delegáti pomocí parametrů typu lze definovat počet a typ vstupní parametry a návratový typ delegáta. `Func`Delegáti jsou velmi užitečné pro zapouzdření uživatelem definované výrazy, které se použijí pro každý prvek v sadě zdrojová data. Představte si třeba <xref:System.Func%601> delegáta, kde je syntaxe:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

Delegát může být vytvořena s podobně jako tento kód

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

kde `int` je vstupní parametr, a `bool` je návratovou hodnotu. Vrácená hodnota je vždy určena v posledním parametru typu. Pokud následující `Func` delegát vyvolán, vrátí hodnotu PRAVDA nebo NEPRAVDA označuje, zda vstupní parametr rovna 5:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

Výraz lambda může taky poskytovat, pokud je typ argumentu <xref:System.Linq.Expressions.Expression%601>, například v operátory standardní dotazu, které jsou definovány v <xref:System.Linq.Queryable> typu. Pokud zadáte <xref:System.Linq.Expressions.Expression%601> argument, argument lambda kompiluje na strom výrazu. Následující příklad používá [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) operátor standardní dotazu.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

Kompilátor může odvodit typ vstupního parametru, nebo jej můžete nastavit také explicitně. Tento výraz lambda konkrétní počty těchto celých čísel (`n`), pokud dělený dva, mít zbytek 1.

Následující příklad vytvoří sekvenci, která obsahuje všechny elementy ve `numbers` pole, které předcházet 9, protože se jedná o první číslo v pořadí, které nesplňují podmínku.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

Následující příklad určuje více vstupních parametrů uzavřené v závorkách. V poli čísla, dokud zjistí číslo, jehož hodnota je menší než jeho pořadové číslo pozice v poli, vrátí metoda všechny elementy.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a>Odvození typu v výrazy lambda ##

Při zápisu lambdas, často není nutné zadávat typ pro vstupní parametry, protože kompilátor můžete odvození typu na základě textu lambda, typy parametrů a dalších faktorech, jak je popsáno v specifikace jazyka C#. Pro většinu standardních operátorů pro dotazování je prvním vstupem typ prvků ve zdrojové sekvenci. Pokud se dotazuje `IEnumerable<Customer>`, pak je potřeba odvodit vstupní proměnné `Customer` objekt, což znamená, máte přístup k jeho metody a vlastnosti:

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

Obecná pravidla pro odvození typu pro lambdas jsou:

- Výraz lambda musí obsahovat stejný počet parametrů jako typ delegátu.

- Všechny vstupní argumenty v argument lambda musí být implicitně převést na jeho odpovídající parametr delegáta.

- Vrácená hodnota lambda (pokud existuje) musí být implicitně převoditelná na návratový typ delegátu.

Výrazy lambda nemají vlastní určený typ, protože systém běžných typů nezná vnitřní pojem „výraz lambda“. Někdy je však vhodné hovořit neformálně o „typu“ výrazu lambda. V těchto případech se typ odkazuje na typ delegáta nebo <xref:System.Linq.Expressions.Expression> typ výrazu lambda je převeden.

## <a name="variable-scope-in-lambda-expressions"></a>Rozsah proměnné ve výrazech lambda ##

Lambdas mohou odkazovat na *vnější proměnné* (viz [anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)), které jsou v oboru v metody, která definuje funkci lambda, nebo v oboru v typu, který obsahuje výraz lambda. Proměnné, které jsou zachyceny tímto způsobem, jsou uloženy pro použití ve výrazu lambda i v případě, že proměnné by jinak přesáhly rozsah platnosti a bylo by vynuceno uvolnění paměti. Vnější proměnná musí být jednoznačně přiřazena dříve, než může být upotřebena ve výrazu lambda. Následující příklad ukazuje, tato pravidla.

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 Následující pravidla se vztahují na rozsah proměnné ve výrazu lambda:

- Proměnná, která je zachycena, nebude uvolněna z paměti, dokud delegát, který na ni odkazuje, nebude mít oprávnění k uvolňování paměti.

- Proměnné, které jsou představeny v rámci výrazu lambda, nejsou viditelné ve vnější metodě.

- Výraz lambda nemůže zaznamenat přímo `ref` nebo `out` parametr z metody nadřazených.

- Příkaz return ve výrazu lambda nezpůsobí vrácení ohraničující metody.

- Nemůže obsahovat výraz lambda `goto` příkaz `break` prohlášení, nebo `continue` příkaz, který je uvnitř funkce lambda, pokud příkaz přechod cíl je mimo blok. Je také chybou mít příkaz skoku mimo blok funkce lambda, pokud je cíl uvnitř bloku.

## <a name="see-also"></a>Viz také ##

[LINQ (Language-Integrated Query)](../standard/using-linq.md)   
[Anonymní metody](programming-guide/statements-expressions-operators/anonymous-methods.md)   
[Stromy výrazů](expression-trees.md)
