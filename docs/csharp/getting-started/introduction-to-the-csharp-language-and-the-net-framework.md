---
title: Úvod do jazyka C# a rozhraní .NET Framework
description: Naučte se základy c# a .NET. Získejte přehled jazyka C# a ekosystému .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 9feca97b141b08d418f6833374cbe3c7a0c26d66
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805784"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Úvod do jazyka C# a rozhraní .NET Framework

C# je elegantní a typově bezpečný objektově orientovaný jazyk, který vývojářům umožňuje vytvářet různé zabezpečené a robustní aplikace, které běží v rozhraní .NET Framework. Pomocí jazyka C# můžete vytvářet klientské aplikace systému Windows, webové služby XML, distribuované součásti, aplikace klient-server, databázové aplikace a mnoho dalšího. Visual C# poskytuje pokročilý editor kódu, pohodlné návrháře uživatelského rozhraní, integrovaný ladicí program a mnoho dalších nástrojů, které usnadňují vývoj aplikací na základě jazyka C# a rozhraní .NET Framework.  
  
> [!NOTE]
> Visual C# dokumentace předpokládá, že máte pochopení základní koncepty programování. Pokud jste úplný začátečník, můžete prozkoumat Visual C# Express, který je k dispozici na webu. Můžete také využít knihy a webové prostředky o jazyce C# naučit praktické programovací dovednosti.  
  
## <a name="c-language"></a>jazyk C#

Syntaxe jazyka C# je vysoce expresivní, ale je také jednoduchá a snadno se učí. Syntaxe složené závorky jazyka C# bude okamžitě rozpoznatelná pro všechny osoby obeznámené s c, c++ nebo javou. Vývojáři, kteří znají některý z těchto jazyků jsou obvykle schopni začít pracovat produktivně v jazyce C# v krátkém čase. Syntaxe jazyka C# zjednodušuje mnoho složitostí jazyka C++ a poskytuje výkonné funkce, jako jsou typy s možnou hodnotou null, výčty, delegáty, výrazy lambda a přímý přístup do paměti. C# podporuje obecné metody a typy, které poskytují zvýšenou bezpečnost typů a výkon a iterátory, které umožňují implementátorům tříd kolekce definovat vlastní iterace chování, které jsou jednoduché použití podle klientského kódu. Výrazy linq (Language Integrated Query) činí z dotazu silného typu konstrukci jazyka první třídy.  
  
 Jako objektově orientovaný jazyk c# podporuje koncepty zapouzdření, dědičnosti a polymorfismu. Všechny proměnné a metody, `Main` včetně metody, vstupníbod aplikace, jsou zapouzdřeny v rámci definice třídy. Třída může dědit přímo z jedné nadřazené třídy, ale může implementovat libovolný počet rozhraní. Metody, které přepsat virtuální metody v `override` nadřazené třídě vyžadují klíčové slovo jako způsob, jak se vyhnout náhodnému předefinování. V C# struct je jako odlehčené třídy; jedná se o typ přidělený zásobníkem, který může implementovat rozhraní, ale nepodporuje dědičnost.  
  
 Kromě těchto základních principů zaměřených na objekty c# usnadňuje vývoj softwarových komponent prostřednictvím několika inovativních jazykových konstrukcí, včetně následujících:  
  
- Zapouzdřené podpisy metod nazývané *delegáty*, které umožňují oznámení událostí bezpečného typu.  
  
- Vlastnosti, které slouží jako přistupující objekty pro proměnné soukromých členů.  
  
- Atributy, které poskytují deklarativní metadata o typech za běhu.  
  
- Komentáře k dokumentaci vřádku XML.  
  
- Jazykově integrovaný dotaz (LINQ), který poskytuje integrované funkce dotazů napříč různými zdroji dat.  
  
 Pokud máte k interakci s jiným softwarem systému Windows, jako jsou objekty COM nebo nativní Win32 Knihovny DLL, můžete to provést v jazyce C# prostřednictvím procesu s názvem "Interop". Interop umožňuje c# programy dělat téměř cokoliv, co nativní aplikace Jazyka C++ může dělat. C# dokonce podporuje ukazatele a koncept "nebezpečný" kód pro ty případy, ve kterých je kritický přímý přístup do paměti.  
  
 Proces sestavení jazyka C# je jednoduchý ve srovnání s C a C++ a flexibilnější než v jazyce Java. Neexistují žádné samostatné soubory hlaviček a žádný požadavek, aby metody a typy byly deklarovány v určitém pořadí. Zdrojový soubor Jazyka C# může definovat libovolný počet tříd, struktur, rozhraní a událostí.  
  
 Následují další prostředky jazyka C#:  
  
- Dobrý obecný úvod do jazyka naleznete v kapitole 1 [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).  
  
- Podrobné informace o konkrétních aspektech jazyka C# naleznete v [odkazu jazyka C#](../language-reference/index.md).  
  
- Další informace o LINQ naleznete v tématu [LINQ (Language-Integrated Query).](../programming-guide/concepts/linq/index.md)  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 Programy jazyka C# jsou spuštěny v rozhraní .NET Framework, což je integrální součást systému Windows, který zahrnuje systém virtuálního spuštění nazývaný clr (COMMON Language runtime) a jednotnou sadu knihoven tříd. CLR je komerční implementace společné jazykové infrastruktury (CLI) společností Microsoft, což je mezinárodní standard, který je základem pro vytváření prostředí pro provádění a vývoj, ve kterých jazyky a knihovny bezproblémově spolupracují.  
  
 Zdrojový kód napsaný v jazyce C# je zkompilován do [zprostředkujícího jazyka (IL),](../../standard/managed-code.md) který odpovídá specifikaci rozhraní rozhraní. Il kód a prostředky, jako jsou bitmapy a řetězce, jsou uloženy na disku ve spustitelném souboru nazývaném sestavení, obvykle s příponou .exe nebo DLL. Sestavení obsahuje manifest, který poskytuje informace o typech sestavení, verzi, jazykové verzi a požadavcích na zabezpečení.  
  
 Při spuštění programu C# sestavení je načten do CLR, které může provádět různé akce na základě informací v manifestu. Pokud jsou splněny požadavky na zabezpečení, clr provede kompilaci Just-In-Time (JIT) převést il kód na nativní instrukce počítače. CLR také poskytuje další služby související s automatickým uvolňováním paměti, zpracováním výjimek a správou prostředků. Kód, který je spuštěn CLR se někdy označuje jako "spravovaný kód", na rozdíl od "nespravovaného kódu", který je kompilován do nativního strojového jazyka, který se zaměřuje na konkrétní systém. Následující diagram znázorňuje relace kompilace a run-time souborů zdrojového kódu jazyka C#, knihoven tříd rozhraní .NET Framework, sestavení a clr.  
  
 ![Ze zdrojového kódu Jazyka C# do spuštění počítače](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Jazyková interoperabilita je klíčovou funkcí rozhraní .NET Framework. Vzhledem k tomu, že il kód vytvořený kompilátorem jazyka C# odpovídá společné specifikaci typu (CTS), může kód IL generovaný z jazyka C# pracovat s kódem, který byl vygenerován z verzí jazyka .NET jazyka Visual Basic, Visual C++ nebo některého z více než 20 dalších jazyků kompatibilních s CTS. Jedno sestavení může obsahovat více modulů napsaných v různých jazycích .NET a typy se mohou vzájemně odkazovat, jako by byly napsány ve stejném jazyce.  
  
 Kromě služeb běhu obsahuje rozhraní .NET Framework také rozsáhlou knihovnu více než 4000 tříd uspořádaných do oborů názvů, které poskytují širokou škálu užitečných funkcí pro vše od vstupu a výstupu až po manipulaci s řetězci až po analýzu XML až po ovládací prvky Windows Forms. Typická aplikace Jazyka C# používá knihovnu tříd rozhraní .NET Framework k rozsáhlému zpracování běžných "instalatérských" domácích práce.  
  
 Další informace o rozhraní .NET Framework naleznete v [tématu Přehled rozhraní Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Viz také

- [Začínáme s visual c #](/visualstudio/ide/quickstart-csharp-console)
