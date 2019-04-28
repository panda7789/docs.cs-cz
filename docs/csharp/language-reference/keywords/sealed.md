---
title: zapečetěné modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: babad3b07c5faea1381e6af13d3c713122de2332
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660759"
---
# <a name="sealed-c-reference"></a>sealed (Referenční dokumentace jazyka C#)

Při použití na třídu, `sealed` modifikátor zabrání ostatním třídám z něj dědí. V následujícím příkladu třída `B` dědí z třídy `A`, ale žádná třída může dědit z třídy `B`.

```csharp
class A {}
sealed class B : A {}
```

Můžete také použít `sealed` modifikátor na metodu nebo vlastnost, která přepíše virtuální metody nebo vlastnosti v základní třídě. To umožňuje povolit třídy, které jsou odvozeny z vaší třídy a zabránili jejich přepsání konkrétní virtuální metody nebo vlastnosti.

## <a name="example"></a>Příklad

V následujícím příkladu `Z` dědí z `Y` ale `Z` nemůže přepsat virtuální funkci `F` , která je deklarována v `X` a uzavřené v `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Při definování nové metody nebo vlastnosti ve třídě, můžete zabránit odvozená třídy přepsání není deklarací je jako [virtuální](virtual.md).

Jedná se o chybu používat [abstraktní](abstract.md) modifikátor zapečetěnou třídu, protože abstraktní třídy musí být zděděny třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.

Při použití na metodu nebo vlastnost, `sealed` modifikátor musí být vždy použit s [přepsat](override.md).

Protože struktury jsou implicitně zapečetěná, nelze dědit.

Další informace najdete v tématu [dědičnosti](../../programming-guide/classes-and-structs/inheritance.md).

Další příklady najdete v tématu [abstraktní a zapečetěné třídy a členové](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

V předchozím příkladu můžete vyzkoušet dědit od zapečetěné třídy pomocí následujícího příkazu:

`class MyDerivedC: SealedClass {}   // Error`

Výsledek se zobrazí chybová zpráva:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a>Poznámky

Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně byste měli zvážit následující dva body:

- Potenciálních výhod, že odvozené třídy mohou získat prostřednictvím možnost přizpůsobit si své třídy.

- Potenciál odvozené třídy může změnit tříd takovým způsobem, že by už nebude fungovat správně nebo jako očekává.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Abstraktní a uzavřené třídy a jejich členové](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modifikátory](modifiers.md)
- [override](override.md)
- [virtual](virtual.md)