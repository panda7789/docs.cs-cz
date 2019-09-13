---
title: virtuální C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 586e50818fc8ceaad5ca1925c0636b31015d81d4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925376"
---
# <a name="virtual-c-reference"></a>virtual (Referenční dokumentace jazyka C#)

`virtual` Klíčové slovo se používá k úpravě deklarace metody, vlastnosti, indexeru nebo události a umožňuje přepsání v odvozené třídě. Tuto metodu lze například přepsat libovolnou třídou, která ji dědí:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Implementaci virtuálního člena lze změnit [přepsáním členu](override.md) v odvozené třídě. Další informace o použití `virtual` klíčového slova naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a znalost, [kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Poznámky

Je-li vyvolána virtuální metoda, je typ běhu objektu zkontrolován pro přepisující člena. Přepsání členu v největší odvozené třídě je volána, což může být původní člen, pokud žádná odvozená třída přepsala člena.

Ve výchozím nastavení jsou metody nevirtuální. Nemůžete přepsat nevirtuální (non-Virtual) metodu.

`virtual` Modifikátor nelze použít `static`s modifikátory, `abstract`, `private`nebo `override` . Následující příklad ukazuje virtuální vlastnost:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Virtuální vlastnosti se chovají podobně jako abstraktní metody, s výjimkou rozdílů v deklaraci a syntaxi vyvolání.

- Použití `virtual` modifikátoru na statické vlastnosti je chybné.

- Virtuální zděděnou vlastnost lze přepsat v odvozené třídě zahrnutím deklarace vlastnosti, která používá `override` modifikátor.

## <a name="example"></a>Příklad

V tomto příkladu `Shape` třída obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metodu. Různé třídy `Circle`tvarů, jako například `Cylinder`,, `Sphere` a dědí `Shape` třídu a oblast povrchu je vypočítána pro každý obrázek. Každá odvozená třída má svou vlastní implementaci `Area()`přepsání.

Všimněte si, že zděděné `Sphere`třídy `Circle`, `Cylinder` a všechny používají konstruktory, které inicializují základní třídu, jak je znázorněno v následující deklaraci.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Následující program vypočítá a zobrazí příslušnou oblast pro každý obrázek vyvoláním příslušné implementace `Area()` metody v závislosti na objektu, který je spojen s metodou.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [New (modifikátor)](new-modifier.md)
