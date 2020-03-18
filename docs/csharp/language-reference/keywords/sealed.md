---
title: zapečetěný modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 686afd5d9d0394bb1a802551b65083732599f384
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713102"
---
# <a name="sealed-c-reference"></a>sealed (Referenční dokumentace jazyka C#)

Při použití na třídu `sealed` modifikátor zabraňuje dědění jiných tříd z ní. V následujícím příkladu `B` třída dědí z třídy `A`, `B`ale žádná třída může dědit z třídy .

```csharp
class A {}
sealed class B : A {}
```

`sealed` Modifikátor můžete také použít na metodu nebo vlastnost, která přepíše virtuální metodu nebo vlastnost v základní třídě. To umožňuje povolit třídy odvodit z vaší třídy a zabránit jim v přepsání konkrétní virtuální metody nebo vlastnosti.

## <a name="example"></a>Příklad

V následujícím příkladu dědí `Z` z, `Z` `Y` ale `F` nelze přepsat `X` virtuální funkce, která je deklarována a zapečetěna v `Y`.

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

Když definujete nové metody nebo vlastnosti ve třídě, můžete zabránit odvození tříd y jejich přepsání tím, že je nedeklarujete jako [virtuální](virtual.md).

Je chyba použít [abstraktní](abstract.md) modifikátor s zapečetěné třídy, protože abstraktní třída musí být zděděna třídou, která poskytuje implementaci abstraktnímetody nebo vlastnosti.

Při použití na metodu `sealed` nebo vlastnost musí být modifikátor vždy použit s [přepsáním](override.md).

Vzhledem k tomu, že struktury jsou implicitně zapečetěny, nemohou být zděděny.

Další informace naleznete v [tématu Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).

Další příklady naleznete [v tématu Abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).

## <a name="example"></a>Příklad

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

V předchozím příkladu se můžete pokusit dědit z zapečetěné třídy pomocí následujícího příkazu:

`class MyDerivedC: SealedClass {}   // Error`

Výsledkem je chybová zpráva:

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a>Poznámky

Chcete-li zjistit, zda chcete zapečetit třídu, metodu nebo vlastnost, měli byste obecně zvážit následující dva body:

- Potenciální výhody, které odvozené třídy mohou získat díky možnosti přizpůsobit třídu.

- Potenciál, který odvozené třídy může změnit vaše třídy takovým způsobem, že by již pracovat správně nebo podle očekávání.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Statické třídy a jejich členové](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Abstraktní a uzavřené třídy a jejich členové](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Modifikátory](index.md)
- [override](override.md)
- [virtual](virtual.md)
