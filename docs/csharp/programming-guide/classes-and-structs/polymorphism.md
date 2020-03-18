---
title: Polymorfismus - C# Programovací průvodce
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 58980bd0d70d8a778cdb208f56d31ee8465871a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170166"
---
# <a name="polymorphism-c-programming-guide"></a>Polymorfismus (Průvodce programováním v C#)

Polymorfismus je často označován jako třetí pilíř objektově orientovaného programování po zapouzdření a dědičnosti. Polymorfismus je řecké slovo, které znamená "mnoho-formoval" a má dva odlišné aspekty:
  
- Za běhu objekty odvozené třídy mohou být považovány za objekty základní třídy v místech, jako jsou parametry metody a kolekce nebo pole. Dojde-li k tomuto polymorfismu, deklarovaný typ objektu již není shodný s typem za běhu.
- Základní třídy mohou definovat a implementovat [virtuální](../../language-reference/keywords/virtual.md) *metody*a odvozené třídy je mohou [přepsat,](../../language-reference/keywords/override.md) což znamená, že poskytují vlastní definici a implementaci. Za běhu, když kód klienta volá metodu, CLR vyhledá typ běhu objektu a vyvolá toto přepsání virtuální metody. Ve zdrojovém kódu můžete volat metodu na základní třídy a způsobit odvozené třídy verze metody, které mají být provedeny.

Virtuální metody umožňují pracovat se skupinami souvisejících objektů jednotným způsobem. Předpokládejme například, že máte kreslicí aplikaci, která umožňuje uživateli vytvářet různé druhy obrazců na kreslicí ploše. V době kompilace nevíte, které konkrétní typy obrazců uživatel vytvoří. Aplikace však musí sledovat všechny různé typy obrazců, které jsou vytvořeny a musí je aktualizovat v reakci na akce myši uživatele. Polymorfismus můžete použít k vyřešení tohoto problému ve dvou základních krocích:

1. Vytvořte hierarchii tříd, ve které každá konkrétní třída tvarů pochází ze společné základní třídy.
1. Virtuální metoda slouží k vyvolání příslušné metody pro všechny odvozené třídy prostřednictvím jednoho volání metody základní třídy.

Nejprve vytvořte základní `Shape`třídu s názvem `Rectangle` `Circle`a `Triangle`odvozené třídy, například , a . Pojmenujte třídu `Shape` `Draw`virtuální metodou s názvem a přepište ji v každé odvozené třídě, abyste nakreslili konkrétní tvar, který třída představuje. Vytvořte `List<Shape>` objekt a `Circle` `Triangle`přidejte `Rectangle` k němu a .

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Chcete-li aktualizovat kreslicí plochu, použijte [foreach](../../language-reference/keywords/foreach-in.md) smyčky `Draw` iterát prostřednictvím seznamu a volání metody na každý `Shape` objekt v seznamu. I když každý objekt v seznamu `Shape`má deklarovaný typ , je to typ run-time (přepsané verze metody v každé odvozené třídě), která bude vyvolána.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

V jazyce C# je každý typ polymorfní, protože všechny <xref:System.Object>typy, včetně uživatelem definovaných typů, dědí z .  

## <a name="polymorphism-overview"></a>Přehled polymorfismu

### <a name="virtual-members"></a>Virtuální členové

Když odvozená třída dědí ze základní třídy, získá všechny metody, pole, vlastnosti a události základní třídy. Návrhář odvozené třídy může různé volby pro chování virtuálních metod:

- Odvozená třída může přepsat virtuální členy v základní třídě a definovat nové chování.
- Odvozená třída dědí nejbližší metodu základní třídy bez jejího přepsání, zachování existujícího chování, ale povolení dalších odvozených tříd k přepsání metody.
- Odvozené třídy může definovat nové nevirtuální implementace těchto členů, které skrýt implementace základní třídy.

Odvozená třída může přepsat člen základní třídy pouze v případě, že člen základní třídy je deklarován jako [virtuální](../../language-reference/keywords/virtual.md) nebo [abstraktní](../../language-reference/keywords/abstract.md). Odvozený člen musí použít klíčové slovo [přepsat](../../language-reference/keywords/override.md) explicitně označit, že metoda je určena k účasti na virtuální vyvolání. Následující kód obsahuje příklad:

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Pole nemohou být virtuální. pouze metody, vlastnosti, události a indexery mohou být virtuální. Když odvozená třída přepíše virtuální člen, tento člen je volán i v případě, že instance této třídy je přístupná jako instance základní třídy. Následující kód obsahuje příklad:

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Virtuální metody a vlastnosti umožňují odvozeným třídám rozšířit základní třídu bez nutnosti použití implementace základní třídy metody. Další informace naleznete v [tématu Versioning with the Override and New Keywords](./versioning-with-the-override-and-new-keywords.md). Rozhraní poskytuje jiný způsob, jak definovat metodu nebo sadu metod, jejichž implementace je ponechána na odvozené třídy. Další informace naleznete v [tématu Rozhraní](../interfaces/index.md).

### <a name="hide-base-class-members-with-new-members"></a>Skrýt členy základní třídy s novými členy

Pokud chcete, aby vaše odvozená třída měla člena se stejným názvem jako člen v základní třídě, můžete použít [nové](../../language-reference/keywords/new-modifier.md) klíčové slovo ke skrytí člena základní třídy. Klíčové `new` slovo je umístěn před návratový typ člena třídy, který je nahrazen. Následující kód obsahuje příklad:

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Členové skryté základní třídy mohou být přístupné z kódu klienta přetypování instance odvozené třídy na instanci základní třídy. Například:

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Zabránit odvozeným třídám v přepsání virtuálních členů  

Virtuální členové zůstávají virtuální, bez ohledu na to, kolik tříd byly deklarovány mezi virtuální člen a třídy, která původně deklaroval. Pokud `A` třída deklaruje `B` virtuální člen `A`a `C` třída je `B`odvozena od , a třída je odvozena z , třída `C` dědí virtuální člen a může přepsat, bez ohledu na to, zda třída `B` deklarovala přepsání pro tento člen. Následující kód obsahuje příklad:

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Odvozená třída může zastavit virtuální dědičnost deklarováním přepsání jako [zapečetěné](../../language-reference/keywords/sealed.md). Zastavení dědičnosti `sealed` vyžaduje uvedení `override` klíčového slova před klíčové slovo v deklaraci člena třídy. Následující kód obsahuje příklad:

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

V předchozím příkladu `DoWork` metoda již není virtuální pro `C`všechny třídy odvozené z . Je to stále virtuální pro `C`instance , i když `B` jsou `A`přetypována na typ nebo typ . Zapečetěné metody mohou být nahrazeny odvozenými třídami pomocí klíčového `new` slova, jak ukazuje následující příklad:

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

V `DoWork` tomto případě, pokud `D` je volána `D`pomocí `DoWork` proměnné typu , je volána nová. Pokud proměnná `C`typu `B`, `A` , nebo se `D`používá pro `DoWork` přístup k instanci , volání bude dodržovat `DoWork` pravidla `C`virtuální dědičnosti, směrování těchto volání k implementaci na třídu .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Přístup k virtuálním členům základní třídy z odvozených tříd

Odvozená třída, která nahradila nebo přepsala metodu nebo vlastnost, může stále `base` přistupovat k metodě nebo vlastnosti základní třídy pomocí klíčového slova. Následující kód obsahuje příklad:

```csharp
public class Base
{
    public virtual void DoWork() {/*...*/ }
}
public class Derived : Base
{
    public override void DoWork()
    {
        //Perform Derived's work here
        //...
        // Call DoWork on base class
        base.DoWork();
    }
}
```

Další informace naleznete v [tématu base](../../language-reference/keywords/base.md).

> [!NOTE]
> Doporučuje se, aby `base` virtuální členové použít k volání implementace základní třídy tohoto člena v jejich vlastní implementaci. Umožňuje základní třídy chování umožňuje odvozené třídy soustředit se na implementaci chování specifické pro odvozené třídy. Pokud není volána implementace základní třídy, je na odvozené třídě, aby jejich chování bylo kompatibilní s chováním základní třídy.

## <a name="in-this-section"></a>V tomto oddílu

- [Správa verzí pomocí klíčových slov override a new](./versioning-with-the-override-and-new-keywords.md)
- [Znalost, kdy použít klíčová slova override a new](./knowing-when-to-use-override-and-new-keywords.md)
- [Jak přepsat metodu ToString](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Dědičnost](./inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Metody](./methods.md)
- [Akce](../events/index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Typy](../types/index.md)
