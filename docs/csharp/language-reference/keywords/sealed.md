---
description: Sealed – modifikátor – Referenční dokumentace jazyka C#
title: Sealed – modifikátor – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 5b945503c6f6546f571a2422ae77760da0363b08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136964"
---
# <a name="sealed-c-reference"></a>sealed (Referenční dokumentace jazyka C#)

Při použití na třídu `sealed` zakáže modifikátor dědění z něj jiné třídy. V následujícím příkladu třída `B` dědí z třídy `A` , ale žádná třída nemůže dědit z třídy `B` .

```csharp
class A {}
sealed class B : A {}
```

Můžete také použít `sealed` Modifikátor na metodu nebo vlastnost, která přepíše virtuální metodu nebo vlastnost v základní třídě. To umožňuje, aby třídy byly odvozeny z vaší třídy a aby se zabránilo přepsání specifických virtuálních metod nebo vlastností.

## <a name="example"></a>Příklad

V následujícím příkladu `Z` dědí z, `Y` ale `Z` nemůže přepsat virtuální funkci `F` , která je deklarována v `X` a zapečetěna v `Y` .

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Při definování nových metod nebo vlastností ve třídě můžete zabránit odvození tříd z jejich přepsání jejich jejich deklarováním jako [Virtual](virtual.md).

Použití modifikátoru [abstract](abstract.md) s zapečetěnou třídou je chybné, protože abstraktní třída musí být zděděna třídou, která poskytuje implementaci abstraktních metod nebo vlastností.

Při použití na metodu nebo vlastnost `sealed` musí být modifikátor vždy použit s [přepsáním](override.md).

Protože jsou struktury implicitně zapečetěné, nedají se dědit.

Další informace najdete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).

Další příklady naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

V předchozím příkladu se můžete pokusit dědit z zapečetěné třídy pomocí následujícího příkazu:

`class MyDerivedC: SealedClass {}   // Error`

Výsledkem je chybová zpráva:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Poznámky

Chcete-li určit, zda má být třída, metoda nebo vlastnost zapečetěna, je třeba vzít v úvahu následující dva body:

- Potenciální výhody, které odvozují třídy, mohou získat možnost přizpůsobení vaší třídy.

- Potenciál, který odvozují třídy, může upravit vaše třídy takovým způsobem, že by již nepracovaly správně nebo podle očekávání.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Abstraktní a uzavřené třídy a jejich členové](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modifikátory](index.md)
- [override](override.md)
- [virtual](virtual.md)
