---
title: virtuální - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: eede3359b195661ff89a387e9b226bc970c27942
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612567"
---
# <a name="virtual-c-reference"></a>virtual (Referenční dokumentace jazyka C#)

`virtual` – Klíčové slovo se používá k úpravě deklarace metody, vlastnost, indexer nebo událost a povolit pro přepsání v odvozené třídě. Například tato metoda může být přepsána všechny třídy, která dědí ho:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Implementace virtuální člen může změnit [přepsáním členu](override.md) v odvozené třídě. Další informace o tom, jak používat `virtual` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [vědět, když pomocí přepsání a nových klíčových slov](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Poznámky

Při vyvolání virtuální metody run-time typu objektu se kontroluje u přepsáním členu. Přepsáním členu v nejvíce odvozená třída je voláno, původní člen, který může být žádný odvozená třída má potlačenou člena.

Ve výchozím nastavení jsou nevirtuální metody. Nevirtuální metoda nelze přepsat.

Nelze použít `virtual` modifikátor `static`, `abstract`, `private`, nebo `override` modifikátory. Následující příklad ukazuje virtuální vlastnosti:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Virtuální vlastnosti se chovají stejně jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a volání.

- Jedná se o chybu používat `virtual` modifikátor statickou vlastnost.

- Virtuální zděděnou vlastnost možné přepsat v odvozené třídě včetně, která používá deklarace vlastnosti `override` modifikátor.

## <a name="example"></a>Příklad

V tomto příkladu `Shape` třída obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metody. Jiný tvar třídy, jako například `Circle`, `Cylinder`, a `Sphere` dědit `Shape` třídy a útoku na počítá pro každý obrázek. Každá odvozená třída má svůj vlastní implementaci přepsání `Area()`.

Všimněte si, že zděděné třídy `Circle`, `Sphere`, a `Cylinder` používat konstruktory, které inicializuje základní třídu, jak je znázorněno v následující deklaraci.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Následující program vypočítá a zobrazí příslušné oblasti pro každý obrázek vyvoláním vhodné implementaci pro `Area()` metoda podle objektu, který je přidružený k metodě.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Modifikátory](modifiers.md)
- [Klíčová slova jazyka C#](index.md)
- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [new](new.md)