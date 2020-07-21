---
title: Přehled dynamického jazykového běhového prostředí | Microsoft Docs
description: Přečtěte si přehled dynamického jazykového modulu runtime (DLR) v rozhraní .NET. DLR je běhové prostředí, které přidá sadu služeb pro dynamické jazyky do modulu CLR.
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic language runtime
- IronPython
- DLR
- IronRuby
ms.assetid: f769a271-8aff-4bea-bfab-6160217ce23d
ms.openlocfilehash: 2272bc60af35e3cdec3e1a71bbc6516565b4ec6e
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475148"
---
# <a name="dynamic-language-runtime-overview"></a>Přehled DLR (Dynamic Language Runtime)

Modul *dynamického jazyka* (DLR) je běhové prostředí, které přidává sadu služeb pro dynamické jazyky do modulu CLR (Common Language Runtime). DLR usnadňuje vývoj dynamických jazyků pro spouštění na .NET Framework a přidání dynamických funkcí do staticky typových jazyků.

Dynamické jazyky mohou identifikovat typ objektu v době běhu, zatímco ve staticky typovaném jazyce, jako je C# a Visual Basic (při použití `Option Explicit On` ), je nutné zadat typy objektů v době návrhu. Příklady dynamických jazyků jsou Lispu, Smalltalk, JavaScript, PHP, Ruby, Python, ColdFusion, LUA, Cobra a Groove.

Většina dynamických jazyků poskytuje vývojářům následující výhody:

- Možnost použít smyčku rychlé zpětné vazby (REPL nebo Read-Evaluate-Print Loop). To umožňuje zadat několik příkazů a okamžitě je spustit, aby se zobrazily výsledky.

- Podpora pro vývoj na nejvyšší úrovni a jednodušší vývoj v dolní části. Například při použití přístupu shora dolů můžete volat funkce, které ještě nejsou implementovány, a pak přidat základní implementace, pokud je potřebujete.

- Jednodušší refaktoring a změny kódu, protože v celém kódu nemusíte měnit deklarace statických typů.

Dynamické jazyky vytvářejí Skvělé skriptovací jazyky. Zákazníci můžou snadno rozsazovat aplikace vytvořené pomocí dynamických jazyků s novými příkazy a funkcemi. Dynamické jazyky se také často používají k vytváření webů a testovacích prostředí, údržbě serverových farem, vývoji různých nástrojů a provádění transformací dat.

Účelem DLR je umožnit spuštění systému dynamických jazyků na .NET Framework a zajistit interoperabilitu .NET. DLR přidá dynamické objekty do C# a Visual Basic pro podporu dynamického chování v těchto jazycích a umožňuje jejich vzájemné provozování s dynamickými jazyky.

DLR také pomáhá vytvářet knihovny, které podporují dynamické operace. Například pokud máte knihovnu, která používá objekty XML nebo JavaScript Object Notation (JSON), vaše objekty se mohou zobrazit jako dynamické objekty pro jazyky, které používají DLR. To umožňuje uživatelům knihovny psát syntakticky jednodušší a více přirozený kód pro práci s objekty a přístup ke členům objektu.

Například můžete použít následující kód k zvýšení čítače v jazyce XML v jazyce C#.

`Scriptobj.SetProperty("Count", ((int)GetProperty("Count")) + 1);`

Pomocí DLR můžete použít následující kód místo stejné operace.

`scriptobj.Count += 1;`

Podobně jako CLR, je DLR součástí .NET Framework a je k dispozici s instalačními balíčky .NET Framework a sady Visual Studio. Open source verze DLR je také k dispozici ke stažení na [IronLanguages/DLR](https://github.com/IronLanguages/dlr) úložiště na GitHubu.

> [!NOTE]
> Open source verze DLR má všechny funkce DLR, které jsou součástí sady Visual Studio a .NET Framework. Poskytuje taky další podporu pro implementátory jazyků. Další informace najdete v dokumentaci k úložišti [IronLanguages/DLR](https://github.com/IronLanguages/dlr) na GitHubu.

Příklady jazyků vyvinutých pomocí DLR zahrnují následující:

- Ironpythonu. K dispozici jako open source software z webu [GitHubu](https://github.com/IronLanguages/ironpython2) .

- IronRuby. K dispozici jako open source software z webu [IronRuby](http://ironruby.net/) .

## <a name="primary-dlr-advantages"></a>Primární výhody DLR
 DLR poskytuje následující výhody.

### <a name="simplifies-porting-dynamic-languages-to-the-net-framework"></a>Zjednodušuje přenos do .NET Framework dynamické jazyky.
 DLR umožňuje jazykovým implementátorům vyhnout se vytváření lexikálních analyzátorů, analyzátorů, sémantických analyzátorů, generátorů kódu a dalších nástrojů, které tradičně musely vytvořit sami sebe. Chcete-li použít DLR, musí jazyk vytvořit *stromy výrazů*, které reprezentují kód na úrovni jazyka ve stromové struktuře, rutin pomocníka za běhu a volitelné dynamické objekty, které implementují <xref:System.Dynamic.IDynamicMetaObjectProvider> rozhraní. DLR a .NET Framework automatizují mnoho úloh analýzy kódu a generování kódu. Díky tomu můžou implementátori jazyků soustředit na jedinečné funkce jazyka.

### <a name="enables-dynamic-features-in-statically-typed-languages"></a>Povolí dynamické funkce ve staticky typovaném jazyce.
 Existující .NET Framework jazyky, jako je C# a Visual Basic, mohou vytvářet dynamické objekty a používat je společně se staticky typovými objekty. Například C# a Visual Basic mohou používat dynamické objekty pro HTML, model DOM (Document Object Model) (DOM) a reflexi rozhraní .NET.

### <a name="provides-future-benefits-of-the-dlr-and-net-framework"></a>Poskytuje budoucí výhody DLR a .NET Framework
 Jazyky implementované pomocí DLR můžou těžit z budoucích DLR a vylepšení .NET Framework. Například pokud .NET Framework uvolní novou verzi, která má vylepšený systém uvolňování paměti nebo rychlejší načítání sestavení, jazyky implementované pomocí DLR okamžitě získají stejnou výhodu. Pokud DLR přidá optimalizace, jako je například lepší kompilace, zlepšuje se výkon také pro všechny jazyky implementované pomocí DLR.

### <a name="enables-sharing-of-libraries-and-objects"></a>Umožňuje sdílení knihoven a objektů.
 Objekty a knihovny implementované v jednom jazyce mohou být používány jinými jazyky. DLR také umožňuje vzájemné operace mezi staticky napsanými a dynamickými jazyky. Například jazyk C# může deklarovat dynamický objekt, který používá knihovnu, která je napsána v dynamickém jazyce. Ve stejnou dobu mohou dynamické jazyky používat knihovny z .NET Framework.

### <a name="provides-fast-dynamic-dispatch-and-invocation"></a>Poskytuje rychlé dynamické odeslání a vyvolání.
 DLR poskytuje rychlé provádění dynamických operací podporou pokročilého polymorfního ukládání do mezipaměti. DLR vytvoří pravidla pro operace vazby, které používají objekty pro nezbytné implementace modulu runtime, a poté uloží tato pravidla do mezipaměti, aby nedocházelo k vyčerpání vazeb prostředků během po sobě jdoucích provádění stejného kódu na stejných typech objektů.

## <a name="dlr-architecture"></a>Architektura DLR
 Následující ilustrace znázorňuje architekturu dynamického jazykového modulu runtime.

 ![Přehled architektury dynamického jazykového modulu runtime](./media/dlr-archoverview.png "DLR_ArchOverview") Architektura DLR

 DLR přidá sadu služeb pro modul CLR pro lepší podporu dynamických jazyků. Mezi tyto služby patří následující:

- Stromy výrazů. DLR používá stromy výrazů, které reprezentují sémantiku jazyka. Pro účely tohoto účelu má DLR rozšířené stromy výrazů LINQ, aby zahrnovaly tok řízení, přiřazení a další uzly modelování jazyka. Další informace naleznete v tématu [stromy výrazů (C#)](../../csharp/programming-guide/concepts/expression-trees/index.md) nebo [stromy výrazů (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md).

- Volání do mezipaměti webu. *Web s dynamickým voláním* je místo v kódu, kde provádíte operaci jako `a + b` nebo `a.b()` na dynamických objektech. DLR ukládá do mezipaměti charakteristiky `a` a `b` (obvykle typy těchto objektů) a informace o operaci. Pokud taková operace byla provedena dříve, DLR načte všechny potřebné informace z mezipaměti pro rychlé odeslání.

- Interoperabilita dynamických objektů. DLR poskytuje sadu tříd a rozhraní, které představují dynamické objekty a operace a mohou být použity v modulech pro implementaci jazyka a autorech dynamických knihoven. Mezi tyto třídy a rozhraní patří <xref:System.Dynamic.IDynamicMetaObjectProvider> ,, <xref:System.Dynamic.DynamicMetaObject> <xref:System.Dynamic.DynamicObject> a <xref:System.Dynamic.ExpandoObject> .

DLR používá služby BIND v lokalitách volání ke komunikaci nejen s .NET Framework, ale s jinými infrastrukturami a službami, včetně Silverlight a COM. Pojiva zapouzdřuje sémantiku jazyka a určují, jak provádět operace v lokalitě volání pomocí stromů výrazů. To umožňuje dynamickým a staticky typovým jazykům, které používají DLR ke sdílení knihoven a získání přístupu ke všem technologiím, které DLR podporuje.

## <a name="dlr-documentation"></a>Dokumentace k DLR
 Další informace o tom, jak používat Open Source verzi DLR k přidání dynamického chování do jazyka nebo o tom, jak povolit používání dynamického jazyka s .NET Framework, najdete v dokumentaci k úložišti [IronLanguages/DLR](https://github.com/IronLanguages/dlr/tree/master/Docs) na GitHubu.

## <a name="see-also"></a>Viz také

- <xref:System.Dynamic.ExpandoObject>
- <xref:System.Dynamic.DynamicObject>
- [CLR (Common Language Runtime)](../../standard/clr.md)
- [Stromy výrazů (C#)](../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Stromy výrazů (Visual Basic)](../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Návod: vytváření a používání dynamických objektů](../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
