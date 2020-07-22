---
title: Polymorfismus – Průvodce programováním v C#
description: Seznamte se s polymorfismus, Klíčovým konceptem v objektově orientovaných programovacích jazycích, jako je C#, který popisuje vztah mezi základní a odvozenou třídou.
ms.date: 02/08/2020
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 2a1ca4c498c5885c7d34475405ac83c4cccecd6f
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864121"
---
# <a name="polymorphism-c-programming-guide"></a>Polymorfismus (Průvodce programováním v C#)

Polymorfismus se často označuje jako třetí pilíř objektově orientovaného programování, a to po zapouzdření a dědičnosti. Polymorfismus je řecký Word, který znamená "velký tvar" a má dva odlišné aspekty:
  
- V době běhu lze objekty odvozené třídy považovat za objekty základní třídy v místech, jako jsou parametry metody a kolekce nebo pole. Pokud tato polymorfismua nastane, deklarovaný typ objektu již není totožný s jeho typem za běhu.
- Základní třídy mohou definovat a implementovat [virtuální](../../language-reference/keywords/virtual.md) *metody*a odvozené třídy je mohou [přepsat](../../language-reference/keywords/override.md) , což znamená, že poskytují svou vlastní definici a implementaci. V době běhu, když kód klienta volá metodu, modul CLR vyhledá typ za běhu objektu a vyvolá přepsání virtuální metody. Ve zdrojovém kódu můžete zavolat metodu pro základní třídu a způsobit spuštění odvozené třídy verze metody.

Virtuální metody umožňují pracovat se skupinami souvisejících objektů jednotným způsobem. Předpokládejme například, že máte aplikaci pro kreslení, která umožňuje uživateli vytvářet různé druhy tvarů na kreslicí ploše. V době kompilace neznáte, které konkrétní typy tvarů uživatel vytvoří. Aplikace však musí sledovat všechny různé typy tvarů, které byly vytvořeny, a musí je aktualizovat v reakci na akce myši uživatele. K vyřešení tohoto problému můžete použít polymorfismus ve dvou základních krocích:

1. Vytvořte hierarchii třídy, ve které jsou jednotlivé konkrétní třídy tvarů odvozeny ze společné základní třídy.
1. Použijte virtuální metodu k vyvolání vhodné metody pro jakoukoli odvozenou třídu prostřednictvím jediného volání metody základní třídy.

Nejprve vytvořte základní třídu s názvem `Shape` a odvozené třídy, jako například `Rectangle` , `Circle` a `Triangle` . Poskytněte `Shape` třídě virtuální metodu s názvem `Draw` a přepište ji v každé odvozené třídě pro vykreslení konkrétního tvaru, který třída představuje. Vytvořte `List<Shape>` objekt a přidejte `Circle` `Triangle` do něj objekt,, a `Rectangle` .

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#PolymorphismOverview)]

Chcete-li aktualizovat plochu pro kreslení, použijte smyčku [foreach](../../language-reference/keywords/foreach-in.md) k iterování seznamu a zavolejte `Draw` metodu pro každý `Shape` objekt v seznamu. I když každý objekt v seznamu má deklarovaný typ `Shape` , je typ za běhu (přepsaná verze metody v každé odvozené třídě), která bude vyvolána.

[!code-csharp[Polymorphism overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UsePolymorphism)]

V jazyce C# je každý typ polymorfní, protože všechny typy, včetně uživatelsky definovaných typů, dědí z <xref:System.Object> .  

## <a name="polymorphism-overview"></a>Přehled polymorfismu

### <a name="virtual-members"></a>Virtuální členové

Když odvozená třída dědí ze základní třídy, získá všechny metody, pole, vlastnosti a události základní třídy. Návrhář odvozené třídy může lišit možnosti pro chování virtuálních metod:

- Odvozená třída může přepsat virtuální členy v základní třídě a definovat nové chování.
- Odvozená třída dědí nejbližší metodu základní třídy bez přepsání, zachovává stávající chování, ale umožňuje dalším odvozeným třídám přepsat metodu.
- Odvozená třída může definovat novou nevirtuální implementaci těchto členů, kteří skryjí implementace základní třídy.

Odvozená třída může přepsat člen základní třídy pouze v případě, že je člen základní třídy deklarován jako [virtuální](../../language-reference/keywords/virtual.md) nebo [abstraktní](../../language-reference/keywords/abstract.md). Odvozený člen musí použít klíčové slovo [override](../../language-reference/keywords/override.md) k explicitnímu označení toho, že je metoda určena k účasti ve virtuálním vyvolání. Následující kód poskytuje příklad:

[!code-csharp[Virtual overview](~/samples/snippets/csharp/objectoriented/Inheritance.cs#VirtualMethods)]

Pole nemůžou být virtuální. virtuální můžou být jenom metody, vlastnosti, události a indexery. Když odvozená třída přepíše virtuální člen, je tento člen volán i v případě, že instance této třídy je k dispozici jako instance základní třídy. Následující kód poskytuje příklad:

[!code-csharp[Virtual overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#SnippetTestVirtualMethods)]

Virtuální metody a vlastnosti umožňují odvozeným třídám rozšiřuje základní třídu bez nutnosti použití implementace základní třídy metody. Další informace najdete v tématu [Správa verzí pomocí klíčových slov override a New](./versioning-with-the-override-and-new-keywords.md). Rozhraní poskytuje další způsob, jak definovat metodu nebo sadu metod, jejichž implementace je ponechána na odvozené třídy. Další informace naleznete v tématu [rozhraní](../interfaces/index.md).

### <a name="hide-base-class-members-with-new-members"></a>Skrýt členy základní třídy novými členy

Chcete-li, aby vaše odvozená třída měla člena se stejným názvem jako členem v základní třídě, můžete použít klíčové slovo [New](../../language-reference/keywords/new-modifier.md) pro skrytí člena základní třídy. `new`Klíčové slovo je vloženo před návratový typ člena třídy, který se nahrazuje. Následující kód poskytuje příklad:

[!code-csharp[New method overview example](~/samples/snippets/csharp/objectoriented/Inheritance.cs#NewMethods)]

Ke skrytým členům základní třídy je možné přivodit z klientského kódu přetypování instance odvozené třídy na instanci základní třídy. Příklad:

[!code-csharp[New method overview usage](~/samples/snippets/csharp/objectoriented/Inheritance.cs#UseNewMethods)]

### <a name="prevent-derived-classes-from-overriding-virtual-members"></a>Zabránit odvozeným třídám z přepsání virtuálních členů  

Virtuální členové zůstávají virtuální bez ohledu na to, kolik tříd bylo deklarováno mezi virtuálním členem a třídou, která ji původně deklarovala. Pokud třída `A` deklaruje virtuální člen a třída je `B` odvozena z třídy `A` a třída je `C` odvozena z `B` třídy, třída `C` zdědí virtuálního člena a může jej přepsat bez ohledu na to, zda třída `B` deklarovala přepsání pro daného člena. Následující kód poskytuje příklad:

[!code-csharp[Basic hierarchy](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#FirstHierarchy)]

Odvozená třída může zastavit virtuální dědičnost deklarací override jako [sealed](../../language-reference/keywords/sealed.md). Zastavování dědičnosti vyžaduje vložení `sealed` klíčového slova před `override` klíčové slovo v deklaraci člena třídy. Následující kód poskytuje příklad:

[!code-csharp[A sealed overridden member](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#SealedOverride)]

V předchozím příkladu již metoda není typu `DoWork` Virtual pro žádnou třídu odvozenou z `C` . Je stále virtuální pro instance `C` , i když jsou přetypování na typ `B` nebo typ `A` . Zapečetěné metody lze nahradit odvozenými třídami pomocí `new` klíčového slova, jak ukazuje následující příklad:

[!code-csharp[New method declaration](~/samples/snippets/csharp/objectoriented/Hierarchy.cs#NewDeclaration)]

V tomto případě, pokud `DoWork` je volána při `D` použití proměnné typu `D` , `DoWork` je volána nová. Pokud proměnná typu `C` , `B` nebo `A` je použita pro přístup k instanci `D` , volání metody `DoWork` bude následovat pravidla virtuální dědičnosti, směrování těchto volání do implementace `DoWork` třídy na třídu `C` .

### <a name="access-base-class-virtual-members-from-derived-classes"></a>Přístup k virtuálním členům základní třídy z odvozených tříd

Odvozená třída, která nahradila nebo přepsala metodu nebo vlastnost, může stále přistupovat k metodě nebo vlastnosti základní třídy pomocí `base` klíčového slova. Následující kód poskytuje příklad:

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

Další informace naleznete v tématu [Base](../../language-reference/keywords/base.md).

> [!NOTE]
> Doporučuje se, aby virtuální členové použili `base` k volání implementace základní třídy tohoto člena ve své vlastní implementaci. V případě, že dojde k chování základní třídy, umožňuje odvozeným třídám soustředit se na implementaci konkrétního chování, které je specifické pro odvozenou třídu. Pokud není volána implementace základní třídy, je až do odvozené třídy, aby jejich chování bylo kompatibilní s chováním základní třídy.

## <a name="in-this-section"></a>V této části

- [Správa verzí pomocí klíčových slov override a new](./versioning-with-the-override-and-new-keywords.md)
- [Znalost, kdy použít klíčová slova override a new](./knowing-when-to-use-override-and-new-keywords.md)
- [Jak potlačit metodu ToString](./how-to-override-the-tostring-method.md)

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Dědičnost](./inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Metody](./methods.md)
- [Události](../events/index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Typy](../types/index.md)
