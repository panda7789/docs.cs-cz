---
title: výnos kontextové klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712777"
---
# <a name="yield-c-reference"></a>yield (Referenční dokumentace jazyka C#)

Při použití `yield` [kontextové klíčové slovo](index.md#contextual-keywords) v příkazu, označíte, že metoda, operátor nebo `get` přistupující objekt, ve kterém se zobrazí, je iterátor. Použití `yield` k definování iterátoru odebere potřebu explicitní extra třídy (třída, která obsahuje <xref:System.Collections.Generic.IEnumerator%601> stav pro výčt, <xref:System.Collections.IEnumerable> viz <xref:System.Collections.IEnumerator> příklad) při implementaci a vzor pro vlastní typ kolekce.

Následující příklad ukazuje dvě formy `yield` příkazu.

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a>Poznámky

Příkaz se `yield return` používá k vrácení každého prvku po jednom.

Sekvence vrácená z metody iterátoru může být spotřebována pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ. Každá iterace `foreach` smyčky volá metodu iterátoru. Když `yield return` je dosaženo příkazu v metodě `expression` iterátoru, je vrácena a aktuální umístění v kódu je zachována. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.

K ukončení `yield break` iterace můžete použít příkaz.

Další informace o iterátorech naleznete v [tématu Iterators](../../iterators.md).

## <a name="iterator-methods-and-get-accessors"></a>Metody Iterator a získat přístupové metody

Deklarace iterátoru musí splňovat následující požadavky:

- Návratový typ <xref:System.Collections.IEnumerable>musí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>být <xref:System.Collections.Generic.IEnumerator%601>, , , nebo .

- Deklarace nemůže mít žádné [parametry v](in-parameter-modifier.md) [ref](ref.md) nebo [out.](out-parameter-modifier.md)

Typ `yield` iterátoru, který <xref:System.Collections.IEnumerable> vrátí <xref:System.Collections.IEnumerator> `object`nebo je .  Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601>nebo , musí být implicitní převod z `yield return` typu výrazu v příkazu na parametr obecného typu .

Nemůžete zahrnout `yield return` nebo `yield break` prohlášení v:

- [Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).

- Metody, které obsahují nebezpečné bloky. Další informace naleznete v tématu [nebezpečné](unsafe.md).

## <a name="exception-handling"></a>Zpracování výjimek

Příkaz `yield return` nemůže být umístěn v bloku try-catch. Příkaz `yield return` může být umístěn v bloku try příkazu try-finally.

Příkaz `yield break` může být umístěn v bloku try nebo catch bloku, ale ne nakonec bloku.

Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, `finally` je proveden blok v metodě iterátoru.

## <a name="technical-implementation"></a>Technická realizace

Následující kód vrátí `IEnumerable<string>` metodu iterátoru a potom iteruje prostřednictvím jejích prvků.

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

Volání `MyIteratorMethod` neprovede tělo metody. Místo toho volání `IEnumerable<string>` vrátí `elements` do proměnné.

V iteraci `foreach` smyčky <xref:System.Collections.IEnumerator.MoveNext%2A> je metoda `elements`volána . Toto volání provede `MyIteratorMethod` tělo, `yield return` dokud není dosaženo dalšího příkazu. Výraz vrácený `yield return` příkazem určuje nejen hodnotu `element` proměnné pro spotřebu podle těla <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`smyčky, ale `IEnumerable<string>`také vlastnost , která je .

Na každé další `foreach` iteraci smyčky provádění těla iterátoru pokračuje od místa, kde `yield return` přestal, opět zastavení, když dosáhne příkazu. Smyčka `foreach` je dokončena po dosažení konce metody iterátoru nebo příkazu. `yield break`

## <a name="example"></a>Příklad

Následující příklad má `yield return` příkaz, který `for` je uvnitř smyčky. Každá iterace těla příkazu `foreach` v metodě `Main` vytvoří volání funkce iterátoru. `Power` Každé volání funkce iterátoru pokračuje k dalšímu `yield return` spuštění příkazu, ke kterému `for` dochází během další iterace smyčky.

Návratový typ metody iterátoru <xref:System.Collections.IEnumerable>je , což je typ rozhraní iterátoru. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a>Příklad

Následující příklad ukazuje `get` přistupující objekt, který je iterátor. V příkladu `yield return` každý příkaz vrátí instanci uživatelem definované třídy.

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [foreach, in](foreach-in.md)
- [Iterátory](../../iterators.md)
