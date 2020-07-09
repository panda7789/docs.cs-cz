---
title: Úvod do jazyka C# a rozhraní .NET Framework
description: Seznamte se se základy C# a .NET. Získejte přehled o jazyce C# a ekosystému .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 55b90d10a1d8ac8534ba98e1cc5af906d69822a6
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100831"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Úvod do jazyka C# a .NET Framework

C# je elegantní a typově bezpečný objektově orientovaný jazyk, který umožňuje vývojářům vytvářet nejrůznější zabezpečené a robustní aplikace, které běží v ekosystému .NET. Ekosystém .NET se skládá ze všech implementací rozhraní .NET, včetně, ale ne omezení do [.NET Core](../../core/index.yml), a [.NET Framework](../../framework/index.yml). Tento článek se zaměřuje na .NET Framework. Jazyk C# můžete použít k vytváření klientských aplikací pro Windows, webových služeb XML, distribuovaných komponent, aplikací klient-server, databázových aplikací a mnohem mnohem více.

> [!NOTE]
> Dokumentace k jazyku Visual C# předpokládá, že máte znalosti základních konceptů programování. Pokud jste zcela začátečník, možná budete chtít prozkoumat Visual C# Express, který je k dispozici na webu. Můžete také využít výhod knih a webových prostředků týkajících se jazyka C# a seznámit se s praktickými znalostmi programování.

## <a name="c-language"></a>jazyk C#

Syntaxe jazyka C# je vysoce expresná, ale je také jednoduchá a snadno se učí. Syntaxe složené závorky jazyka C# bude okamžitě rozpoznána pro kohokoli, kdo zná jazyk C, C++ nebo Java. Vývojáři, kteří znají některý z těchto jazyků, obvykle můžou v krátké době začít pracovat v jazyce C#. Syntaxe jazyka C# zjednodušuje mnoho složitých prvků jazyka C++ a poskytuje výkonné funkce, jako jsou typy s možnou hodnotou null, výčty, delegáty, výrazy lambda a přímý přístup do paměti. Jazyk C# podporuje obecné metody a typy, které poskytují zvýšenou bezpečnost typů a výkon a iterátory, které umožňují implementátorům tříd kolekcí definovat vlastní chování iterací, které je jednoduché pro použití klientským kódem. Výrazy LINQ (Language-Integrated Query) přidávají dotaz silného typu na konstrukci jazyka první třídy.

Jazyk C# podporuje koncepty zapouzdření, dědičnosti a polymorfismus jako objektově orientovaného jazyka. Všechny proměnné a metody, včetně `Main` metody, vstupního bodu aplikace, jsou zapouzdřeny v rámci definice třídy. Třída může dědit přímo z jedné nadřazené třídy, ale může implementovat libovolný počet rozhraní. Metody, které přepisují virtuální metody v nadřazené třídě, vyžadují `override` klíčové slovo jako způsob, jak se vyhnout náhodnému předefinování. V jazyce C# je struktura podobně jako odlehčená třída; Jedná se o typ přidělený zásobníkem, který může implementovat rozhraní, ale nepodporuje dědění.

Kromě těchto základních principů orientovaných na objekty umožňuje C# snadno vyvíjet softwarové komponenty prostřednictvím několika inovativních jazykových konstrukcí, včetně následujících:

- Zapouzdřené podpisy metod označované jako *Delegáti*, které umožňují typově bezpečná oznámení o událostech.
- Vlastnosti, které slouží jako přístupové objekty pro soukromé proměnné členů.
- Atributy, které poskytují deklarativní metadata o typech v době běhu.
- Vložené dokumentační komentáře XML.
- LINQ (Language-Integrated Query), které poskytuje integrované možnosti dotazování napříč různými zdroji dat.

Pokud je nutné pracovat s jiným softwarem Windows, jako jsou objekty COM nebo nativní knihovny DLL Win32, můžete to provést v jazyce C# prostřednictvím procesu nazývaného "Interoperabilita". Interoperabilita umožňuje programům C# provádět téměř cokoli, co může provést nativní aplikace v jazyce C++. C# podporuje i ukazatele a koncept "nebezpečného" kódu pro případy, kdy je důležité přímý přístup do paměti.

Proces sestavení v jazyce C# je jednoduchý v porovnání s jazyky C a C++ a flexibilnější než v jazyce Java. Neexistují žádné samostatné hlavičkové soubory a nejsou požadovány, aby metody a typy byly deklarovány v určitém pořadí. Zdrojový soubor jazyka C# může definovat libovolný počet tříd, struktur, rozhraní a událostí.

Níže jsou uvedené další zdroje v jazyce C#:

- Dobrý obecný úvod k jazyku naleznete v kapitole 1 [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).
- Podrobné informace o konkrétních aspektech jazyka C# naleznete v [Referenční příručce jazyka c#](../language-reference/index.md).
- Další informace o LINQ naleznete v tématu [LINQ (jazykově integrovaný dotaz)](../programming-guide/concepts/linq/index.md).

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

Programy v jazyce C# běží na .NET Framework, nedílnou součást systému Windows, která zahrnuje virtuální spouštěcí systém nazvaný modul CLR (Common Language Runtime) a jednotnou sadu knihoven tříd. CLR je komerční implementace od Microsoftu v rámci společné jazykové infrastruktury (CLI), což je mezinárodní standard, který je základem pro vytváření prostředí pro spouštění a vývoj, ve kterém jazyky a knihovny spolupracují bez problémů.

Zdrojový kód napsaný v jazyce C# je zkompilován do [mezilehlého jazyka (IL)](../../standard/managed-code.md) , který odpovídá specifikaci rozhraní příkazového řádku. Kód IL a prostředky, jako jsou bitmapy a řetězce, jsou uloženy na disku ve spustitelném souboru nazývaném sestavení, obvykle s příponou. exe nebo. dll. Sestavení obsahuje manifest, který poskytuje informace o typech sestavení, verzi, jazykové verzi a požadavky na zabezpečení.

Při spuštění programu v jazyce C# je sestavení načteno do modulu CLR, který může provádět různé akce na základě informací v manifestu. V případě splnění požadavků zabezpečení pak modul CLR provede kompilaci JIT (just-in-time) k převedení kódu IL na nativní instrukce počítače. CLR také poskytuje další služby související s automatickým uvolňováním paměti, zpracováním výjimek a správou prostředků. Kód, který je spuštěn modulem CLR, se někdy označuje jako "spravovaný kód", na rozdíl od "nespravovaného kódu", který je zkompilován do nativního strojového jazyka, který cílí na konkrétní systém. Následující diagram znázorňuje vztahy za běhu a dobu běhu souborů zdrojového kódu jazyka C#, knihovny tříd .NET Framework, sestavení a CLR.

![Od zdrojového kódu C# k provedení počítače](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

Interoperabilita jazyka je klíčovou funkcí .NET Framework. Vzhledem k tomu, že kód IL generovaný kompilátorem jazyka C# odpovídá specifikaci CTS (Common Type Specification), kód IL generovaný z jazyka C# může pracovat s kódem, který byl vygenerován z verzí rozhraní .NET Visual Basic, Visual C++ nebo z více než 20 dalších jazyků odpovídajících specifikaci CTS. Jedno sestavení může obsahovat více modulů napsaných v různých jazycích .NET a typy mohou odkazovat na sebe, jako kdyby byly napsány ve stejném jazyce.

Kromě běhových služeb .NET Framework obsahuje také rozsáhlou knihovnu více než 4000 tříd uspořádaných do oborů názvů, které poskytují širokou škálu užitečných funkcí pro vše od vstupu a výstupu souborů k manipulaci s řetězci do analýzy XML pro model Windows Forms ovládací prvky. Typická aplikace jazyka C# používá rozsáhlou knihovnu tříd .NET Framework pro zpracování běžných "rutinních" instalací.

Další informace o .NET Framework najdete v tématu [Přehled služby Microsoft .NET Framework](../../framework/get-started/overview.md).

## <a name="see-also"></a>Viz také

- [Začínáme s Visual C #](/visualstudio/ide/quickstart-csharp-console)
