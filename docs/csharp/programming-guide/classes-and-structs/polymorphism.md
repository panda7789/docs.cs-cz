---
title: Polymorfismus – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, polymorphism
- polymorphism [C#]
ms.assetid: 086af969-29a5-4ce8-a993-0b7d53839dab
ms.openlocfilehash: 4f65082ad5094eb0aab28edeb06790a9af4019c6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714734"
---
# <a name="polymorphism-c-programming-guide"></a>Polymorfismus (Průvodce programováním v C#)
Polymorfismus se často označuje jako třetí pilíř objektově orientovaného programování, a to po zapouzdření a dědičnosti. Polymorfismus je řecký Word, který znamená "velký tvar" a má dva odlišné aspekty:  
  
- V době běhu lze objekty odvozené třídy považovat za objekty základní třídy v místech, jako jsou parametry metody a kolekce nebo pole. Pokud k tomu dojde, deklarovaný typ objektu již není totožný s jeho typem za běhu.  
  
- Základní třídy mohou definovat a implementovat [virtuální](../../language-reference/keywords/virtual.md) *metody*a odvozené třídy je mohou [přepsat](../../language-reference/keywords/override.md) , což znamená, že poskytují svou vlastní definici a implementaci. V době běhu, když kód klienta volá metodu, modul CLR vyhledá typ za běhu objektu a vyvolá přepsání virtuální metody. Proto ve vašem zdrojovém kódu můžete zavolat metodu pro základní třídu a způsobit spuštění odvozené třídy verze metody.  
  
 Virtuální metody umožňují pracovat se skupinami souvisejících objektů jednotným způsobem. Předpokládejme například, že máte aplikaci pro kreslení, která umožňuje uživateli vytvářet různé druhy tvarů na kreslicí ploše. V době kompilace neznáte, které konkrétní typy tvarů uživatel vytvoří. Aplikace však musí sledovat všechny různé typy tvarů, které byly vytvořeny, a musí je aktualizovat v reakci na akce myši uživatele. K vyřešení tohoto problému můžete použít polymorfismus ve dvou základních krocích:  
  
1. Vytvořte hierarchii třídy, ve které jsou jednotlivé konkrétní třídy tvarů odvozeny ze společné základní třídy.  
  
2. Použijte virtuální metodu k vyvolání vhodné metody pro jakoukoli odvozenou třídu prostřednictvím jediného volání metody základní třídy.  
  
 Nejprve vytvořte základní třídu s názvem `Shape`a odvozené třídy jako `Rectangle`, `Circle`a `Triangle`. Poskytněte třídu `Shape` virtuální metodu nazvanou `Draw`a přepište ji v každé odvozené třídě pro vykreslení konkrétního tvaru, který třída představuje. Vytvořte objekt `List<Shape>` a přidejte do něj kruh, trojúhelník a obdélník. Chcete-li aktualizovat plochu pro kreslení, použijte smyčku [foreach](../../language-reference/keywords/foreach-in.md) k iterování seznamu a zavolejte metodu `Draw` u každého objektu `Shape` v seznamu. I když každý objekt v seznamu má deklarovaný typ `Shape`, je typ za běhu (přepsaná verze metody v každé odvozené třídě), která bude vyvolána.  
  
 [!code-csharp[csProgGuideInheritance#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#50)]  
  
 V C#je každý typ polymorfní, protože všechny typy, včetně uživatelsky definovaných typů, dědí z <xref:System.Object>.  
  
## <a name="polymorphism-overview"></a>Přehled polymorfismu  
  
### <a name="virtual-members"></a>Virtuální členové  
 Když odvozená třída dědí ze základní třídy, získá všechny metody, pole, vlastnosti a události základní třídy. Návrhář odvozené třídy může zvolit, zda se má  
  
- přepsat virtuální členy v základní třídě,  
  
- Zdědit nejbližší metodu základní třídy bez přepsání  
  
- Definujte novou nevirtuální implementaci těchto členů, kteří skryjí implementace základní třídy.  
  
 Odvozená třída může přepsat člen základní třídy pouze v případě, že je člen základní třídy deklarován jako [virtuální](../../language-reference/keywords/virtual.md) nebo [abstraktní](../../language-reference/keywords/abstract.md). Odvozený člen musí použít klíčové slovo [override](../../language-reference/keywords/override.md) k explicitnímu označení toho, že je metoda určena k účasti ve virtuálním vyvolání. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#20)]  
  
 Pole nemůžou být virtuální. virtuální můžou být jenom metody, vlastnosti, události a indexery. Když odvozená třída přepíše virtuální člen, je tento člen volán i v případě, že instance této třídy je k dispozici jako instance základní třídy. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#21)]  
  
 Virtuální metody a vlastnosti umožňují odvozeným třídám rozšiřuje základní třídu bez nutnosti použití implementace základní třídy metody. Další informace najdete v tématu [Správa verzí pomocí klíčových slov override a New](./versioning-with-the-override-and-new-keywords.md). Rozhraní poskytuje další způsob, jak definovat metodu nebo sadu metod, jejichž implementace je ponechána na odvozené třídy. Další informace naleznete v tématu [rozhraní](../interfaces/index.md).  
  
### <a name="hiding-base-class-members-with-new-members"></a>Skrytí členů základní třídy novými členy  
 Pokud chcete, aby měl váš odvozený člen stejný název jako člen v základní třídě, ale nechcete, aby se účastnil ve virtuálním vyvolání, můžete použít klíčové slovo [New](../../language-reference/keywords/new-modifier.md) . Klíčové slovo `new` je vloženo před návratový typ člena třídy, který se nahrazuje. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#18)]  
  
 Skryté členy základní třídy lze stále přihlašovat z klientského kódu přetypováním instance odvozené třídy do instance základní třídy. Příklad:  
  
 [!code-csharp[csProgGuideInheritance#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#19)]  
  
### <a name="preventing-derived-classes-from-overriding-virtual-members"></a>Prevence odvozených tříd od přepsání virtuálních členů  
 Virtuální členové zůstávají virtuální neomezeně, bez ohledu na to, kolik tříd bylo deklarováno mezi virtuálním členem a třídou, která ji původně deklarovala. Pokud třída A deklaruje virtuální člen a třída B je odvozena z třídy a třída C je odvozena z B, třída C dědí virtuální člen a má možnost ho přepsat, bez ohledu na to, zda třída B deklaruje přepsání pro daného člena. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#22)]  
  
 Odvozená třída může zastavit virtuální dědičnost deklarací override jako [sealed](../../language-reference/keywords/sealed.md). To vyžaduje vložení klíčového slova `sealed` před klíčovým slovem `override` v deklaraci člena třídy. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#24)]  
  
 V předchozím příkladu je `DoWork` metody již nevirtuální pro žádnou třídu odvozenou z jazyka C. Je stále Virtual pro instance C, i když jsou přetypování na typ B nebo typ A. zapečetěné metody lze nahradit odvozenými třídami pomocí klíčového slova `new`, jak ukazuje následující příklad:  
  
 [!code-csharp[csProgGuideInheritance#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#25)]  
  
 V tomto případě, pokud je `DoWork` volána na D pomocí proměnné typu D, je volána nová `DoWork`. Pokud proměnná typu C, B nebo A se používá pro přístup k instanci D, volání `DoWork` bude následovat pravidla virtuální dědičnosti, směrování těchto volání do implementace `DoWork` na třídu C.  
  
### <a name="accessing-base-class-virtual-members-from-derived-classes"></a>Přístup k virtuálním členům základní třídy z odvozených tříd  
 Odvozená třída, která nahradila nebo přepsala metodu nebo vlastnost, může stále přistupovat k metodě nebo vlastnosti základní třídy pomocí klíčového slova `base`. Následující kód poskytuje příklad:  
  
 [!code-csharp[csProgGuideInheritance#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#26)]  
  
 Další informace naleznete v tématu [Base](../../language-reference/keywords/base.md).  
  
> [!NOTE]
> Doporučuje se, aby virtuální členové používali `base` k volání implementace základní třídy tohoto člena ve vlastní implementaci. V případě, že dojde k chování základní třídy, umožňuje odvozeným třídám soustředit se na implementaci konkrétního chování, které je specifické pro odvozenou třídu. Pokud není volána implementace základní třídy, je až do odvozené třídy, aby jejich chování bylo kompatibilní s chováním základní třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Správa verzí pomocí klíčových slov override a new](./versioning-with-the-override-and-new-keywords.md)  
  
- [Znalost, kdy použít klíčová slova override a new](./knowing-when-to-use-override-and-new-keywords.md)  
  
- [Jak přepsat metodu ToString](./how-to-override-the-tostring-method.md)
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Dědičnost](./inheritance.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Metody](./methods.md)
- [Události](../events/index.md)
- [Vlastnosti](./properties.md)
- [Indexery](../indexers/index.md)
- [Typy](../types/index.md)
