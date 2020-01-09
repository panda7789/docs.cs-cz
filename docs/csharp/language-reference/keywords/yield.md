---
title: kontextové klíčové slovo yield C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712777"
---
# <a name="yield-c-reference"></a>yield (Referenční dokumentace jazyka C#)

Při použití [klíčového slova `yield` kontextové](index.md#contextual-keywords) v příkazu označíte, že metoda, operátor nebo přistupující objekt `get`, ve kterém se zobrazí, je iterátor. Použití `yield` k definování iterátoru odstraní nutnost explicitní třídy navíc (třída, která obsahuje stav pro výčet, viz <xref:System.Collections.Generic.IEnumerator%601> pro příklad) při implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> vzoru pro vlastní typ kolekce.

Následující příklad ukazuje dva formy příkazu `yield`.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Poznámky

Pomocí příkazu `yield return` můžete vracet každý prvek po jednom.

Sekvenci vrácenou metodou iterátoru lze spotřebovat pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ. Každá iterace `foreach` smyčky volá metodu iterátoru. Při dosažení `yield return`ho příkazu v metodě iterátoru se vrátí `expression` a aktuální umístění v kódu je zachováno. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.

K ukončení iterace můžete použít příkaz `yield break`.

Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody iterátoru a přistupující objekty get

Deklarace iterátoru musí splňovat následující požadavky:

- Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.

- Deklarace nemůže [mít žádné parametry](in-parameter-modifier.md) [ref](ref.md) nebo [out](out-parameter-modifier.md) .

`yield` typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object`.  Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601>, musí existovat implicitní převod z typu výrazu v příkazu `yield return` na parametr obecného typu.

Do těchto příkazů nemůžete zahrnout `yield return` ani `yield break`.

- [Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).

- Metody, které obsahují nebezpečné bloky. Další informace najdete v tématu [unsafe](unsafe.md).

## <a name="exception-handling"></a>Ošetření výjimek

Příkaz `yield return` se nemůže nacházet v bloku try-catch. Příkaz `yield return` lze umístit do bloku try příkazu try-finally.

Příkaz `yield break` může být umístěn v bloku try nebo bloku catch, ale ne v bloku finally.

Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, je spuštěn blok `finally` v metodě iterátoru.

## <a name="technical-implementation"></a>Technická implementace

Následující kód vrátí `IEnumerable<string>` z metody iterátoru a poté projde jeho prvky.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Volání `MyIteratorMethod` nespustí tělo metody. Místo toho volání vrátí `IEnumerable<string>` do proměnné `elements`.

V iteraci `foreach` smyčky je <xref:System.Collections.IEnumerator.MoveNext%2A> metoda volána pro `elements`. Toto volání provede text `MyIteratorMethod` až do chvíle, kdy se dosáhne dalšího příkazu `yield return`. Výraz vrácený příkazem `yield return` určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také vlastnost <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`, což je `IEnumerable<string>`.

Při každé následující iteraci `foreach` smyčky pokračuje v provádění tohoto textu iterátoru, kde se nachází, a znovu se zastaví, až dosáhne příkazu `yield return`. Cyklus `foreach` končí, když je dosaženo konce metody iterátoru nebo příkazu `yield break`.

## <a name="example"></a>Příklad

Následující příklad obsahuje příkaz `yield return`, který je uvnitř smyčky `for`. Každá iterace těla příkazu `foreach` v metodě `Main` vytvoří volání funkce iterátoru `Power`. Každé volání funkce iterátoru pokračuje na další provedení příkazu `yield return`, ke kterému dojde během další iterace `for` smyčky.

Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable>, což je typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Příklad

Následující příklad ukazuje přistupující objekt `get`, který je iterátorem. V příkladu každý příkaz `yield return` vrací instanci uživatelsky definované třídy.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iterátory](../../iterators.md)
