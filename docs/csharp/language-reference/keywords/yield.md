---
title: klíčové slovo yield – referenční informace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: d3fe4cf92ca17457bd541f092f5d146ba6c1c095
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794413"
---
# <a name="yield-c-reference"></a>yield (Referenční dokumentace jazyka C#)

Při použití `yield` [klíčového slova kontextové](index.md#contextual-keywords) v příkazu označíte, že metoda, operátor nebo `get` přistupující objekt, ve kterém se zobrazí, je iterátor. Použití `yield` k definování iterátoru odstraní nutnost explicitní třídy extra (třída, která obsahuje stav pro výčet, viz <xref:System.Collections.Generic.IEnumerator%601> příklad) při implementaci vzor <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> pro vlastní typ kolekce.

Následující příklad ukazuje dva formy `yield` příkazu.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Poznámky

Použijete `yield return` příkaz k vrácení každého prvku v jednom okamžiku.

Sekvenci vrácenou metodou iterátoru lze spotřebovat pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ. Každá iterace `foreach` smyčky volá metodu iterátoru. Je- `yield return` li v metodě iterátoru dosaženo příkazu, `expression` je vráceno a aktuální umístění v kódu je uchováno. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.

K ukončení iterace `yield break` můžete použít příkaz.

Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iterátoru a přistupující objekty get

Deklarace iterátoru musí splňovat následující požadavky:

- Návratový typ musí <xref:System.Collections.IEnumerable>být, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo. <xref:System.Collections.Generic.IEnumerator%601>

- Deklarace nemůže [mít žádné parametry](in-parameter-modifier.md) [ref](ref.md) nebo [out](out-parameter-modifier.md) .

`yield` Typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object`.  Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601>, musí být implicitní převod z typu výrazu v `yield return` příkazu na parametr obecného typu.

Nemůžete zahrnout `yield return` příkaz `yield break` ani do:

- [Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).

- Metody, které obsahují nebezpečné bloky. Další informace najdete v tématu [unsafe](unsafe.md).

## <a name="exception-handling"></a>Ošetření výjimek

`yield return` Příkaz se nemůže nacházet v bloku try-catch. `yield return` Příkaz lze umístit do bloku try příkazu try-finally.

`yield break` Příkaz se může nacházet v bloku try nebo bloku catch, ale ne v bloku finally.

Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, je spuštěn `finally` blok v metodě iterátoru.

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

V iteraci `foreach` smyčky je <xref:System.Collections.IEnumerator.MoveNext%2A> metoda volána pro. `elements` Toto volání provede tělo `MyIteratorMethod` až do dosažení dalšího `yield return` příkazu. Výraz `yield return` vrácený příkazem určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost objektu `elements`, což je. `IEnumerable<string>`

Při každém následném opakování `foreach` smyčky pokračuje provádění textu iterátoru z místa, kde bylo ponecháno, opětovné zastavení při dosažení `yield return` příkazu. `foreach` Smyčka skončí po dosažení konce metody iterátoru nebo `yield break` příkazu.

## <a name="example"></a>Příklad

Následující příklad obsahuje `yield return` příkaz, který je uvnitř `for` smyčky. Každá iterace těla `foreach` příkazu v `Main` metodě vytvoří volání funkce `Power` iterátoru. Každé volání funkce iterátoru pokračuje k dalšímu provedení `yield return` příkazu, ke kterému dojde během další iterace `for` smyčky.

Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable>, což je typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.

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
