---
title: virtuální - C# Reference
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173455"
---
# <a name="virtual-c-reference"></a>virtual (Referenční dokumentace jazyka C#)

Klíčové `virtual` slovo se používá k úpravě metody, vlastnosti, indexeru nebo deklarace události a umožňuje, aby byla přepsána v odvozené třídě. Například tato metoda může být přepsána libovolnou třídou, která ji dědí:

```csharp
public virtual double Area()
{
    return x * y;
}
```

Implementace virtuálního člena může být změněna [přepsáním člena](override.md) v odvozené třídě. Další informace o použití `virtual` klíčového slova naleznete v [tématu Správa verzí s přepsáním a novými klíčovými slovy](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [Informace o tom, kdy použít přepsání a Nová klíčová slova](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Poznámky

Při vyvolání virtuální metody je typ za běhu objektu zkontrolován pro přepsání člena. Je volán přepsání členu v nejvíce odvozené třídě, což může být původní člen, pokud žádná odvozená třída nepřepsala člen.

Ve výchozím nastavení jsou metody nevirtuální. Nelze přepsat nevirtuální metodu.

`virtual` Modifikátor nelze použít `static` `abstract`s `private`modifikátory , , nebo `override` modifikátory. Následující příklad ukazuje virtuální vlastnost:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Virtuální vlastnosti se chovají jako virtuální metody, s výjimkou rozdílů v syntaxi deklarace a vyvolání.

- Je chyba použít `virtual` modifikátor na statickou vlastnost.

- Virtuální zděděná vlastnost může být přepsána v odvozené `override` třídě zahrnutím deklarace vlastnosti, která používá modifikátor.

## <a name="example"></a>Příklad

V tomto `Shape` příkladu třída obsahuje `x`dvě `y`souřadnice , a `Area()` virtuální metoda. Různé třídy `Circle`tvarů, například , `Cylinder`a `Sphere` dědí třídu `Shape` a plocha povrchu se vypočítá pro každý obrázek. Každá odvozená třída má vlastní `Area()`implementaci přepsání .

Všimněte si, `Circle`že `Sphere`zděděné třídy , a `Cylinder` všechny používají konstruktory, které inicializují základní třídu, jak je znázorněno v následující deklaraci.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Následující program vypočítá a zobrazí příslušnou oblast pro každý obrázek vyvoláním `Area()` příslušné implementace metody podle objektu, který je přidružen k metodě.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
- [Abstraktní](abstract.md)
- [override](override.md)
- [nový (modifikátor)](new-modifier.md)
