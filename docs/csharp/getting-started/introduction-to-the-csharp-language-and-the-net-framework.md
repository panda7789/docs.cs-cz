---
title: Úvod do jazyka C# a rozhraní .NET Framework
description: Seznamte se se C# základy a .NET. Získejte přehled o C# jazyce a ekosystému .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 995362667ed0a203112744f03a036eabbcb784c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608310"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Úvod do jazyka C# a rozhraní .NET Framework

C#je elegantní a typově bezpečný objektově orientovaný jazyk, který umožňuje vývojářům vytvářet různé zabezpečené a robustní aplikace, které běží na .NET Framework. Pomocí C# nástroje můžete vytvářet klientské aplikace pro Windows, webové služby XML, distribuované součásti, aplikace klient-server, databázové aplikace a spoustu dalších věcí. Visual C# poskytuje pokročilý editor kódu, praktické návrháře uživatelského rozhraní, integrovaný ladicí program a mnoho dalších nástrojů, které usnadňují vývoj aplikací na základě C# jazyka a .NET Framework.  
  
> [!NOTE]
> Dokumentace k C# vizuálu předpokládá, že máte přehled o základních konceptech programování. Pokud jste zcela začátečník, možná budete chtít prozkoumat Visual C# Express, který je k dispozici na webu. Můžete také využít výhod knih a webových prostředků a seznámit C# se s praktickými znalostmi programování.  
  
## <a name="c-language"></a>Jazyk C#

 C#syntaxe je velice expresná, ale je také jednoduchá a snadno se učí. Syntaxe složené závorky C# se dá okamžitě rozpoznat pro všechny známé pomocí jazyka C C++ nebo Java. Vývojáři, kteří znají některý z těchto jazyků, obvykle mohou začít pracovat v C# rámci velmi krátkého času. C#syntaxe zjednodušuje mnoho složitosti C++ a poskytuje výkonné funkce, jako jsou typy hodnot s možnou hodnotou null, výčty, delegáti, výrazy lambda a přímý přístup do paměti, které se v jazyce Java nenašly. C#podporuje obecné metody a typy, které poskytují zvýšenou bezpečnost typů a výkon a iterátory, které umožňují implementátorům tříd kolekcí definovat vlastní chování iterací, které je jednoduché pro použití klientským kódem. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]výrazy vytvářejí dotaz silně typované konstrukce jazyka první třídy.  
  
 Jako objektově orientovaný jazyk C# podporuje koncepty zapouzdření, dědičnosti a polymorfismu. Všechny proměnné a metody, včetně `Main` metody, vstupního bodu aplikace, jsou zapouzdřeny v rámci definice třídy. Třída může dědit přímo z jedné nadřazené třídy, ale může implementovat libovolný počet rozhraní. Metody, které přepisují virtuální metody v nadřazené třídě, `override` vyžadují klíčové slovo jako způsob, jak se vyhnout náhodnému předefinování. V C#je struktura jako odlehčená třída; Jedná se o typ přidělený zásobníkem, který může implementovat rozhraní, ale nepodporuje dědění.  
  
 Kromě těchto základních principů orientovaných na objekty C# usnadňuje vývoj softwarových komponent prostřednictvím několika inovativních jazykových konstrukcí, včetně následujících:  
  
- Zapouzdřené podpisy metod označované jako *Delegáti*, které umožňují typově bezpečná oznámení o událostech.  
  
- Vlastnosti, které slouží jako přístupové objekty pro soukromé proměnné členů.  
  
- Atributy, které poskytují deklarativní metadata o typech v době běhu.  
  
- Vložené dokumentační komentáře XML.  
  
- [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]poskytuje integrované možnosti dotazování napříč různými zdroji dat.  
  
 Pokud potřebujete pracovat s jiným softwarem Windows, jako jsou objekty COM nebo nativní knihovny DLL Win32, můžete to provést C# pomocí procesu s názvem "Interoperabilita". Interoperabilita C# umožňuje programům provádět téměř cokoli, co C++ může provést nativní aplikace. C#dokonce podporuje ukazatele a pojem "nebezpečný" kód pro případy, kdy přímý přístup do paměti je naprosto kritický.  
  
 Proces C# sestavení je jednoduchý v porovnání s jazykem C C++ a a flexibilnější než v jazyce Java. Neexistují žádné samostatné hlavičkové soubory a nejsou požadovány, aby metody a typy byly deklarovány v určitém pořadí. C# Zdrojový soubor může definovat libovolný počet tříd, struktur, rozhraní a událostí.  
  
 Níže jsou uvedené další C# zdroje informací:  
  
- Dobrý obecný úvod k jazyku naleznete v kapitole 1 [ C# specifikace jazyka](../language-reference/language-specification/index.md).  
  
- Podrobné informace o konkrétních aspektech C# jazyka najdete v [ C# referenčních](../language-reference/index.md)informacích.  
  
- Další informace o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]naleznete v tématu [LINQ (jazykově integrovaný dotaz)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 C#programy spouštěné v .NET Framework, nedílnou součást systému Windows, která zahrnuje virtuální spouštěcí systém nazvaný modul CLR (Common Language Runtime) a jednotnou sadu knihoven tříd. CLR je komerční implementace od Microsoftu v rámci společné jazykové infrastruktury (CLI), což je mezinárodní standard, který je základem pro vytváření prostředí pro spouštění a vývoj, ve kterém jazyky a knihovny spolupracují bez problémů.  
  
 Zdrojový kód napsaný C# v je zkompilován do [mezilehlého jazyka (IL)](../../standard/managed-code.md) , který odpovídá specifikaci rozhraní příkazového řádku. Kód IL a prostředky, jako jsou bitmapy a řetězce, jsou uloženy na disku ve spustitelném souboru nazývaném sestavení, obvykle s příponou. exe nebo. dll. Sestavení obsahuje manifest, který poskytuje informace o typech sestavení, verzi, jazykové verzi a požadavky na zabezpečení.  
  
 Po spuštění C# programu je sestavení načteno do CLR, což může provádět různé akce na základě informací v manifestu. Poté, pokud jsou splněny požadavky na zabezpečení, provede modul CLR kompilaci just in time (JIT) k převedení kódu IL na nativní instrukce počítače. CLR také poskytuje další služby související s automatickým uvolňováním paměti, zpracováním výjimek a správou prostředků. Kód, který je spuštěn modulem CLR, se někdy označuje jako "spravovaný kód", na rozdíl od "nespravovaného kódu", který je zkompilován do nativního strojového jazyka, který cílí na konkrétní systém. Následující diagram znázorňuje vztahy za běhu a dobu běhu souborů C# zdrojového kódu, knihovny tříd .NET Framework, sestavení a CLR.  
  
 ![Ze zdrojového&#35; kódu jazyka C k provedení počítače](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Interoperabilita jazyka je klíčovou funkcí .NET Framework. Vzhledem k tomu, že kód IL C# generovaný kompilátorem odpovídá specifikaci CTS (Common Type Specification), kód Il generovaný z C# může pracovat s kódem, který byl vygenerován z verzí rozhraní .NET Visual Basic, vizuálu C++nebo z více než 20 dalších Jazyky vyhovující standardu CTS. Jedno sestavení může obsahovat více modulů napsaných v různých jazycích .NET a typy mohou odkazovat na sebe stejně, jako kdyby byly napsány ve stejném jazyce.  
  
 Kromě běhových služeb .NET Framework obsahuje také rozsáhlou knihovnu více než 4000 tříd uspořádaných do oborů názvů, které poskytují širokou škálu užitečných funkcí pro vše od vstupu a výstupu souborů k manipulaci s řetězci do XML. analýza, pro model Windows Forms ovládací prvky. Typická C# aplikace často používá knihovnu tříd .NET Framework pro zpracování běžných "rutinních" instalací.  
  
 Další informace o .NET Framework najdete v tématu [Přehled služby Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Viz také:

- [C#](../index.md)
- [Začínáme s jazykem Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
