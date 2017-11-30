---
title: "Úvod do jazyka C# a rozhraní .NET Framework"
description: "Přečtěte si základy C# a rozhraní .NET. Získáte přehled o jazyka C# a ekosystém .NET."
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2bc7dfbca102a5d2e891b48b676347822eae56f7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Úvod do jazyka C# a rozhraní .NET Framework
C# je elegantní a bezpečnost typů objektově orientované jazyk, který umožňuje vývojářům vytvářet celou řadu zabezpečené a robustní aplikace, které běží na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Můžete C# k vytvoření klienta Windows aplikace, webové služby XML, distribuované součásti, klient-server, databázových aplikací a mnoho mnohem víc. Visual C# poskytuje pokročilé kód editoru, návrháři pohodlný uživatelského rozhraní, integrované ladicí program a mnoho dalších nástrojů usnadňují vývoj aplikací na základě jazyka C# a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> [!INCLUDE[csprcs](~/includes/csprcs-md.md)] Dokumentace předpokládá, že máte představu o základní koncepty programování. Pokud jste dokončení Začátečník, můžete chtít prozkoumat [!INCLUDE[csprcsxpr](~/includes/csprcsxpr-md.md)], která je k dispozici na webu. Můžete také využít knih a webové zdroje informací o C# další praktické znalosti programování.  
  
## <a name="c-language"></a>Jazyk C#  
 Syntaxe jazyka C# je vysoce výrazovou, ale je také jednoduchý a snadno se další informace. Složené závorky syntaxe jazyka C# bude okamžitě rozpoznatelném nikomu obeznámeni s C, C++ nebo Java. Vývojáři, kteří znají některý z těchto jazyků je obvykle moct začít umožňují zvýšení produktivity práce v jazyce C# během velmi krátké doby. C# – syntaxe zjednodušuje mnoho složitosti C++ a poskytuje funkce, jako jsou typy hodnot s povolenou hodnotou Null, vytváření výčtů a delegáti, lambda – výrazy a přímý přístup do paměti, které nebyly nalezeny v jazyce Java. C# podporuje obecné metody a typy, které poskytují zvýšenou typu zabezpečení a výkonu a iterátory, které umožňují implementátory typu tříd kolekce k definování vlastní iterace chování, které jsou jednoduché na používání kódem na straně klienta. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]výrazy proveďte silného typu dotaz konstrukce prvotřídní jazyk.  
  
 Jako objektově orientovaný jazyk C# podporuje koncepty zapouzdření, dědičnost a polymorfismus. Všechny proměnné a metody, včetně `Main` metoda, vstupní bod aplikace, jsou zapouzdřené v rámci definice tříd. Třídy mohou dědit přímo z jedné nadřazené třídy, ale může ho implementovat libovolný počet rozhraní. Metody, které potlačí virtuální metody v nadřazené třídě vyžadují `override` – klíčové slovo jako způsob, jak zabránit náhodnému předefinování. V jazyce C# struktury, je stejná jako lehké třídy; je přidělen zásobníku typ, který můžete implementovat rozhraní ale nepodporuje dědičnosti.  
  
 Kromě těchto základních zásad objektově orientované C# usnadňuje vývoj součástí softwaru prostřednictvím několika inovativní jazykové konstrukty, včetně následujících:  
  
-   Zapouzdřené podpisy metoda volána *delegáti*, který povolit oznamování událostí bezpečnost typů.  
  
-   Vlastnosti, které slouží jako přistupující objekty pro privátní členské proměnné.  
  
-   Atributy, které poskytují deklarativní metadata o typech za běhu.  
  
-   Dokumentační komentáře XML vložené.  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]které napříč celou řadu zdrojů dat poskytuje možnosti integrovaného dotazu.  
  
 Pokud máte k interakci s jiným softwarem Windows například objekty modelu COM nebo nativních knihoven DLL Win32, můžete k tomu v jazyce C# prostřednictvím procesu označovaného jako "Zprostředkovatel komunikace s objekty." Zprostředkovatel komunikace s objekty umožňuje programy C# téměř vše, co nativní aplikace C++ můžete udělat. C# i podporuje ukazatelů a konceptu "nezabezpečený" kód pro případy, ve kterých je absolutně nezbytné, přímý přístup do paměti.  
  
 Proces sestavení C# je jednoduchý ve srovnání se C a C++ a flexibilnější než v jazyce Java. Neexistují žádné hlavičky samostatné soubory a nevyžaduje, aby metody a typy deklarovat v určitém pořadí. Zdrojový soubor C# může definovat libovolný počet třídy, struktury, rozhraním a událostem.  
  
 Zde jsou další C# zdroje:  
  
-   Dobrý obecný úvod do jazyka, naleznete v 1 [specifikace jazyka C#](../../csharp/language-reference/language-specification/index.md).  
  
-   Podrobné informace o specifických aspektů jazyka C#, najdete v článku [referenční dokumentace jazyka C#](../../csharp/language-reference/index.md).  
  
-   Další informace o [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], najdete v části [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework  
 C# programy běží [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], nedílnou součástí systému Windows, která obsahuje virtuální spuštění systému názvem common language runtime (CLR) a sada knihovny tříd. Modul CLR je komerční implementace Microsoft common language infrastructure (CLI), mezinárodní standard, který je základem pro vytvoření, spuštění a vývojových prostředí, ve kterých jazycích a knihovny bezproblémově fungovat.  
  
 Zdrojový kód napsaný v jazyce C# zkompilován převodní jazyk (IL), který splňuje specifikace rozhraní příkazového řádku. Kód IL a prostředky, například rastrové obrázky a řetězce, jsou uloženy v názvem sestavení, obvykle s příponou .exe nebo .dll spustitelný soubor na disku. Sestavení obsahuje manifestu, který obsahuje informace o typy sestavení, verzi, jazykovou verzi a požadavky na zabezpečení.  
  
 Při spuštění programu C#, sestavení je načten do modulu CLR, který může mít různé akce na základě informací v manifestu. Poté pokud jsou splněny požadavky na zabezpečení, modulu CLR se provádí pouze v kompilaci time (JIT) převést kód IL nativní počítače pokyny. Modul CLR taky poskytuje další služby související s automatické uvolňování, zpracování výjimek a Správa prostředků. Kód, který se spustí pomocí modulu CLR je někdy označuje jako "spravované kódu" na rozdíl od "nespravovaný kód", který se zkompiluje do nativním jazyce počítače zacílený konkrétního systému. Následující diagram znázorňuje vztahy kompilaci a běhu jazyka C# soubory zdrojového kódu, knihovny tříd rozhraní .NET Framework, sestavení a modulu CLR.  
  
 ![Z C &#35; zdrojový kód pro spuštění počítače](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 Vzájemná funkční spolupráce jazyka je klíčovou funkcí [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Protože kód IL vyprodukované kompilátor jazyka C# odpovídá na běžné specifikace typu (CTS), kód IL vygenerovat z jazyka C# mohou komunikovat s kódem, který byl vytvořen z rozhraní .NET verze jazyka Visual Basic, Visual C++ nebo libovolná z více než 20 kompatibilní se standardem CTS jazyky. Jediné sestavení může obsahovat více modulů, které jsou napsané v různých jazycích .NET a typy může odkazovat navzájem stejně, jako kdyby byly napsány ve stejném jazyce.  
  
 Kromě služby běhu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] také zahrnuje rozsáhlé knihovny víc než 4000 tříd, které jsou uspořádány do obory názvů, které nabízí širokou škálu užitečné funkce pro všechno, co ze souboru vstup a výstup a zacházení s řetězci do formátu XML Analýza pro ovládací prvky Windows Forms. Typická aplikace C# používá [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd hojně pro zpracování běžné chores "jakousi instalaci".  
  
 Další informace o rozhraní .NET Framework najdete v tématu [přehled rozhraní Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Viz také  
 [C#](../../csharp/index.md) [Začínáme s Visual C# a Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
