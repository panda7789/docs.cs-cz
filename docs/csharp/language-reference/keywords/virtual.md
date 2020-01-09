---
title: virtuální C# odkaz
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 47b77792fd3a2b2700ec0734851fdec534361596
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712868"
---
# <a name="virtual-c-reference"></a>virtual (Referenční dokumentace jazyka C#)

Klíčové slovo `virtual` slouží k úpravě deklarace metody, vlastnosti, indexeru nebo události a umožňuje přepsání v odvozené třídě. Tuto metodu lze například přepsat libovolnou třídou, která ji dědí:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Implementaci virtuálního člena lze změnit [přepsáním členu](override.md) v odvozené třídě. Další informace o použití klíčového slova `virtual` naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Poznámky

Je-li vyvolána virtuální metoda, je typ běhu objektu zkontrolován pro přepisující člena. Přepsání členu v největší odvozené třídě je volána, což může být původní člen, pokud žádná odvozená třída přepsala člena.

Ve výchozím nastavení jsou metody nevirtuální. Nemůžete přepsat nevirtuální (non-Virtual) metodu.

Modifikátor `virtual` nelze použít u modifikátorů `static`, `abstract`, `private`nebo `override`. Následující příklad ukazuje virtuální vlastnost:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Virtuální vlastnosti se chovají podobně jako virtuální metody, s výjimkou rozdílů v deklaraci a syntaxi vyvolání.

- Použití modifikátoru `virtual` pro statickou vlastnost je chybné.

- Virtuální zděděnou vlastnost lze přepsat v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor `override`.

## <a name="example"></a>Příklad

V tomto příkladu třída `Shape` obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metodu. Různé třídy tvarů, například `Circle`, `Cylinder`a `Sphere` dědí třídu `Shape` a oblast plocha je vypočítána pro každý obrázek. Každá odvozená třída má svou vlastní implementaci přepsání `Area()`.

Všimněte si, že zděděné třídy `Circle`, `Sphere`a `Cylinder` všechny používají konstruktory, které inicializují základní třídu, jak je znázorněno v následující deklaraci.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Následující program vypočítá a zobrazí příslušnou oblast pro každý obrázek vyvoláním příslušné implementace metody `Area()`, v závislosti na objektu, který je spojen s metodou.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [New (modifikátor)](new-modifier.md)
