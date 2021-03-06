---
description: klíčové slovo yield – referenční informace jazyka C#
title: klíčové slovo yield – referenční informace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141878"
---
# <a name="yield-c-reference"></a>yield (Referenční dokumentace jazyka C#)

Při použití `yield` [klíčového slova kontextové](index.md#contextual-keywords) v příkazu označíte, že metoda, operátor nebo `get` přistupující objekt, ve kterém se zobrazí, je iterátor. Použití `yield` k definování iterátoru odstraní nutnost explicitní třídy extra (třída, která obsahuje stav pro výčet, viz <xref:System.Collections.Generic.IEnumerator%601> příklad) při implementaci <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> vzor a pro vlastní typ kolekce.

Následující příklad ukazuje dva formy `yield` příkazu.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Poznámky

Použijete `yield return` příkaz k vrácení každého prvku v jednom okamžiku.

Sekvenci vrácenou metodou iterátoru lze spotřebovat pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ. Každá iterace `foreach` smyčky volá metodu iterátoru. Je-li `yield return` v metodě iterátoru dosaženo příkazu, `expression` je vráceno a aktuální umístění v kódu je uchováno. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.

`yield break`K ukončení iterace můžete použít příkaz.

Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iterátoru a přistupující objekty get

Deklarace iterátoru musí splňovat následující požadavky:

- Návratový typ musí být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .

- Deklarace nemůže [mít žádné parametry](in-parameter-modifier.md) [ref](ref.md) nebo [out](out-parameter-modifier.md) .

`yield`Typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object` .  Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601> , musí být implicitní převod z typu výrazu v `yield return` příkazu na parametr obecného typu.

Nemůžete zahrnout `yield return` `yield break` příkaz ani do:

- [Lambda výrazy](../operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).

- Metody, které obsahují nebezpečné bloky. Další informace najdete v tématu [unsafe](unsafe.md).

## <a name="exception-handling"></a>Ošetření výjimek

`yield return`Příkaz se nemůže nacházet v bloku try-catch. `yield return`Příkaz lze umístit do bloku try příkazu try-finally.

`yield break`Příkaz se může nacházet v bloku try nebo bloku catch, ale ne v bloku finally.

Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, `finally` je spuštěn blok v metodě iterátoru.

## <a name="technical-implementation"></a>Technická implementace

Následující kód vrátí `IEnumerable<string>` z metody iterátoru a pak projde jeho prvky.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Volání `MyIteratorMethod` nespustí tělo metody. Místo toho volání vrátí `IEnumerable<string>` do `elements` proměnné.

V iteraci `foreach` smyčky <xref:System.Collections.IEnumerator.MoveNext%2A> je metoda volána pro `elements` . Toto volání provede tělo `MyIteratorMethod` až do `yield return` dosažení dalšího příkazu. Výraz vrácený `yield return` příkazem určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost objektu `elements` , což je `IEnumerable<string>` .

Při každém následném opakování `foreach` smyčky pokračuje provádění textu iterátoru z místa, kde bylo ponecháno, opětovné zastavení při dosažení `yield return` příkazu. `foreach`Smyčka skončí po dosažení konce metody iterátoru nebo `yield break` příkazu.

## <a name="example"></a>Příklad

Následující příklad obsahuje `yield return` příkaz, který je uvnitř `for` smyčky. Každá iterace `foreach` těla příkazu v `Main` metodě vytvoří volání `Power` funkce iterátoru. Každé volání funkce iterátoru pokračuje k dalšímu provedení `yield return` příkazu, ke kterému dojde během další iterace `for` smyčky.

Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable> , což je typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `get` přistupující objekt, který je iterátorem. V příkladu každý `yield return` příkaz vrátí instanci uživatelsky definované třídy.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iterátory](../../iterators.md)
