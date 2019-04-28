---
title: Úvod do jazyka C# a rozhraní .NET Framework
description: Naučte se základy C# a .NET. Získejte přehled o jazyce C# a ekosystému .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 28fde47721e6354612ffec557da25c6d3bb775e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672376"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Úvod do jazyka C# a rozhraní .NET Framework

C# je elegantní a typově bezpečný objektově orientované jazyka, který umožňuje vývojářům vytvářet různé zabezpečené a robustní aplikace, které běží na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Můžete C# k vytvoření klienta Windows aplikace, webové služby XML, distribuované součásti, aplikace typu klient server, databázové aplikace a mnohem, mnohem více. Visual C# obsahuje Rozšířený editor kódu, vhodné návrháře uživatelské rozhraní, integrovaný ladicí program a mnoho dalších nástrojů, aby bylo snazší vývoj aplikací založených na jazyce C# a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> Dokumentace k Visual C# se předpokládá, že máte znalosti o základních konceptech programování. Pokud jste úplný Začátečník, můžete chtít prozkoumat Visual C# Express, která je k dispozici na webu. Můžete taky využít výhod knih a webových prostředků o jazyce C# a získat tak praktické znalosti programování.  
  
## <a name="c-language"></a>Jazyk C#

 Syntaxe jazyka C# je vysoce výrazová, ale je také jednoduchá a snadno osvojitelná. Syntaxi využívající složenou jazyka C# bude pozná okamžitě každý, kdo zná C, C++ nebo Java. Vývojáři, kteří znají některý z těchto jazyků jsou obvykle schopni začít produktivně pracovat v jazyce C# ve velmi krátkém čase. Syntaxe jazyka C# zjednodušuje mnoho složitostí jazyka C++ a nabízí účinné funkce, jako jsou typy s možnou hodnotou Null, výčty, delegáti, lambda výrazy a přímý přístup do paměti, což není k dispozici v jazyce Java. C# podporuje obecné metody a typy, které poskytují zvýšení typové bezpečnosti a výkonu a iterátory, které umožňují implementátorům tříd kolekcí definovat vlastní chování iterací, které je jednoduché pro použití kódem na straně klienta. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] výrazy Ujistěte se, dotazy silných typů prvotřídní jazykové konstrukce.  
  
 Jako objektově orientovaný jazyk podporuje jazyk C# koncepty zapouzdření, dědičnosti a polymorfismu. Všechny proměnné a metod, včetně `Main` metodu vstupního bodu aplikace, jsou zapouzdřeny v rámci definice třídy. Třída může dědit přímo od jedné nadřazené třídy, ale může implementovat libovolný počet rozhraní. Metody, které jsou nadřazeny virtuálním metodám v nadřazené třídu vyžadují `override` pro zabránění náhodnému předefinování klíčové slovo. V jazyce C# je struktura jako lehká třída; je to typ přidělený na zásobník, který můžete implementovat rozhraní, ale nepodporuje dědění.  
  
 Kromě těchto základních objektově orientovaných principů C# usnadňuje vývoj softwarových komponent díky několika inovačním jazykovým konstrukcím, včetně následujících:  
  
- Zapouzdřené podpisy metod nazývané *delegáti*, který povolit oznamování událostí typově bezpečné.  
  
- Vlastnosti, které slouží jako přístupové objekty pro proměnné soukromých členů.  
  
- Atributy, které poskytují deklarativní metadata o typech za běhu.  
  
- Dokumentační komentáře XML vložené.  
  
- [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] které poskytuje předdefinované možnosti různých datových zdrojů.  
  
 Pokud potřebujete pracovat s jiným softwarem Windows, jako jsou objekty COM nebo nativními knihovnami DLL Win32, můžete to provést C# prostřednictvím procesu nazývaného "Interoperabilita". Interoperabilita umožňuje programům C# provádět téměř cokoli, co můžete dělat nativní aplikace C++. C# podporuje i ukazatele a koncept "nebezpečného" kódu pro případy, ve kterých je nezbytně nutný přímý přístup do paměti.  
  
 Proces sestavení C# je jednoduchý jazycích C a C++ a flexibilnější než v jazyce Java. Neexistují žádné samostatné hlavičkové soubory a žádný požadavek, metody a typy byly deklarovány v určitém pořadí. Zdrojový soubor jazyka C# může definovat libovolný počet tříd, struktur, rozhraní a události.  
  
 Následují další zdroje jazyka C#:  
  
- Dobrý obecný úvod do jazyka, najdete v kapitole 1 [specifikace jazyka C#](../../csharp/language-reference/language-specification/index.md).  
  
- Podrobné informace o specifických aspektech jazyka C# najdete v tématu [referenční dokumentace jazyka C#](../../csharp/language-reference/index.md).  
  
- Další informace o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], naleznete v tématu [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 Spouštět programy jazyka C# [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], součásti systému Windows, která obsahuje virtuální systém spouštění volá common language runtime (CLR) a ucelenou sadu knihoven tříd. CLR představuje komerční implementaci Microsoft common language infrastructure (CLI), mezinárodního standardu, který je základem pro vytváření, provádění a vývoj prostředí, ve kterých jazyky a knihovny fungují společně bez problémů.  
  
 Zdrojového kódu napsaného v jazyce C# je zkompilován intermediate language (IL), který odpovídá specifikaci CLI. Kód IL a prostředky, například rastrové obrázky a řetězce, jsou uloženy na disku do spustitelného souboru nazývaného jako sestavení, obvykle s příponou .exe nebo .dll. Sestavení obsahuje manifest, který poskytuje informace o typech sestavení, verzi, jazykovou verzi a požadavky na zabezpečení.  
  
 Když je spuštěn program C#, je načten do CLR, který může mít různé akce na základě informací v manifestu sestavení. Potom Pokud jsou splněny požadavky na zabezpečení, modul CLR provede pouze v time (JIT) kompilaci kódu IL převod na nativních strojové instrukce. CLR také poskytuje jiné služby související s automatickým uvolňování paměti, zpracování výjimek a správu prostředků. Kód, který je proveden součástí CLR je někdy označovány jako "spravovaný kód" na rozdíl od "nespravovaného kódu", který je kompilován do nativního strojového jazyka, který se zaměřuje na konkrétní systém. Následující diagram znázorňuje vztahy během kompilace a za běhu jazyka C# souborů se zdrojovým kódem, knihovny tříd rozhraní .NET Framework, sestavení, a CLR.  
  
 ![From C&#35; zdrojový kód pro spuštění počítače](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Vzájemná spolupráce jazyků je klíčovou funkcí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Protože kód IL produkovaný kompilátorem jazyka C# odpovídá na běžné specifikaci typů (CTS), kód IL generovaný jazykem C# můžete pracovat s kódem, který byl vytvořen .NET verzí jazyka Visual Basic, Visual C++ nebo některý z více než 20 dalších jazyků kompatibilních s CTS. Jediné sestavení může obsahovat více modulů napsaných v různých jazycích .NET, a typy mohou odkazovat na sebe navzájem tak, jako kdyby byly napsány ve stejném jazyce.  
  
 Kromě služeb běhu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] také obsahuje rozsáhlou knihovnu více než 4000 tříd, které jsou uspořádány do oborů názvů, který nabízí celou řadu užitečných funkcí pro všechno, co ze souboru vstup a výstup a manipulaci s řetězci XML Analýza pro ovládací prvky Windows Forms. Typická aplikace C# používá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd pro zpracování běžných "údržbových" činností.  
  
 Další informace o rozhraní .NET Framework najdete v tématu [přehled rozhraní Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Viz také:

- [C#](../../csharp/index.md)
- [Začínáme s jazykem Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
