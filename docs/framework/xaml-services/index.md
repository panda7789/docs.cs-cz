---
title: XAML Services
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
caps.latest.revision: 13
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f36f22e8bf68520f5f57280d33cf37990feb2df6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="xaml-services"></a>XAML Services
Toto téma popisuje možnosti sadu technologií, označuje jako rozhraní .NET Framework XAML Services. Většina služeb a rozhraní API popsané se nacházejí v sestavení System.Xaml, což je sestavení zavedené [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sadu sestavení .NET core. Služby zahrnují čtení a zápis, třídy schématu a podporu schématu, objekty Factory zapisujících třídy, vnitřní podporu jazyka XAML a další funkce jazyka XAML.  
  
## <a name="about-this-documentation"></a>O této dokumentace  
 Rámcová dokumentace pro rozhraní .NET Framework XAML Services předpokládá, že máte předchozí zkušenosti s jazykem XAML a jak se mohou vztahovat na určité rozhraní, například [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] nebo modelu Windows Workflow Foundation, nebo konkrétní technologie funkce oblasti, například sestavení přizpůsobení funkce ve <xref:Microsoft.Build.Framework.XamlTypes>. Tato dokumentace se nebude pokoušet vysvětlují základní informace o XAML jako značka jazyka, XAML syntaxe terminologie nebo jiného materiálu úvodní. Místo toho tato dokumentace se zaměřuje na konkrétně pomocí rozhraní .NET Framework XAML Services, která jsou povolena v knihovně System.Xaml sestavení. Většina těchto rozhraní API jsou pro scénáře integrace jazyka XAML a rozšíření. To může zahrnovat některé z následujících:  
  
-   Rozšíření možnosti základní čtečky XAML nebo zapisovače XAML (zpracování datový proud uzlu XAML přímo; odvozování vlastní XAML čtečky nebo zapisovač XAML).  
  
-   Definování XAML použitelné vlastních typů, které nemají žádný konkrétní framework závislosti a zapisujících typy, které mají nesou jejich XAML zadejte charakteristiky systému rozhraní .NET Framework XAML Services.  
  
-   Hostování jako součást aplikace, jako je vizuálního návrháře nebo interaktivní editor pro XAML značek zdroje XAML čtečky nebo XAML zapisovače.  
  
-   Zápis převodníky hodnot XAML (rozšíření značek; převaděčů typů pro vlastní typy).  
  
-   Definování vlastních kontext schématu XAML (pomocí technik, alternativní načtení sestavení pro základní typ zdroje; pomocí techniky vyhledávání známé typy místo vždy odrážející sestavení; pomocí načíst sestavení koncepty, které nepoužívají modulu CLR `AppDomain` a svůj model zabezpečení).  
  
-   Rozšíření základní typ systému XAML.  
  
-   Pomocí `Lookup` nebo `Invoker` techniky k ovlivnění XAML zadejte systému a jak se vyhodnocují podklady u typu.  
  
 Pokud hledáte úvodní materiály v XAML jako jazyk, můžete vyzkoušet [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Toto téma popisuje XAML pro cílovou skupinu, která je nové, na [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a také pomocí značek XAML a funkce jazyka XAML. Další užitečné dokument je úvodní informace v [specifikace jazyka XAML](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Rozhraní .NET framework XAML Services a System.Xaml v architektuře .NET  
 V předchozích verzích [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)], podporu pro jazykové funkce jazyka XAML byl implementované architektury, které založený na [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], modelu Windows Workflow Foundation a Windows Communication Foundation (WCF)) a proto nejrůznější v jeho chování a rozhraní API používá v závislosti na tom, jaké konkrétní framework jste používali. To zahrnuté XAML analyzátor a jeho objekt graf vytvoření mechanismus, vnitřní funkce jazyka XAML, podporu serializace a tak dále.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework XAML Services a sestavení System.Xaml definovat většinu co je potřeba pro podporu funkce jazyka XAML. To zahrnuje základní třídy pro XAML čtení a zápis XAML. Nejdůležitější funkce přidána do rozhraní .NET Framework XAML Services, který se nenachází v žádné z implementace XAML konkrétní rozhraní je reprezentace systému typu pro jazyk XAML. Typ systému reprezentace uvede XAML objektově orientované takovým způsobem, který soustředí na možnostech XAML bez nutnosti převádět závislosti na specifické možnosti rozhraní.  
  
 Systém typů XAML není omezeno značek formuláře nebo spuštění specifika původu XAML; ani je omezena žádné konkrétní základní typ systému. Systém typů XAML zahrnuje reprezentace objektu pro typy, členy, kontexty schématu XAML, koncepty úrovni XML a další koncepty jazyka XAML nebo vnitřní funkce jazyka XAML. Pomocí nebo rozšíření systému typ XAML umožňuje odvozeny od třídy jako XAML čtení a zápis XAML a rozšířit funkce reprezentace XAML do určité funkce, které jsou povolené rozhraní, technologie nebo aplikaci, která využívá nebo vysílá XAML. Koncept kontext schématu XAML umožňuje operace zápisu praktické objekt grafu z kombinace na XAML objekt zapisovače implementace, systém typů zálohování technologie, oznámené pomocí informací o sestavení v kontextu a uzlu XAML zdroj. Další informace o koncept schématu XAML. v tématu [výchozí kontext schématu XAML a kontext schématu XAML WPF](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Datové proudy uzlu XAML, XAML čtení a zápis XAML  
 Pro pochopení role, kterou hraje rozhraní .NET Framework XAML Services v relaci mezi jazyk XAML a konkrétní technologie, které používají jako jazyk XAML, je vhodné se seznámit s koncept datový proud uzlu XAML a jak daný koncept obrazce rozhraní API a terminologie. Datový proud uzlu XAML je koncepční zprostředkující mezi znázornění jazyka XAML a grafu objektu, který představuje XAML nebo definuje.  
  
-   Čtečka XAML je entita, která zpracovává XAML v některé formuláře a vytvoří datový proud uzlu XAML. V rozhraní API je čtečku XAML reprezentována základní třídy <xref:System.Xaml.XamlReader>.  
  
-   Zapisovač XAML je entita, která zpracovává datový proud uzlu XAML a vytváří něco jiného. V rozhraní API je zapisovač XAML reprezentována základní třídy <xref:System.Xaml.XamlWriter>.  
  
 Dva nejběžnější scénáře zahrnující XAML jsou načítání XAML pro vytvoření instance grafu objektu a ukládání grafu objektů z aplikace nebo nástroje a vytváření znázornění XAML (obvykle ve značek formulář uložit jako textový soubor). Načítání XAML a vytvoření grafu objektu je často uvedené v této dokumentaci jako cestu zatížení. Uložení nebo serializaci existující grafu objektu do jazyka XAML se často označuje v této dokumentaci jako uložení cestu.  
  
 Nejběžnějším typem zatížení cesty lze popsat následujícím způsobem:  
  
-   Začněte s znázornění XAML ve formátu XML s kódováním UTF a uložit jako textový soubor.  
  
-   Načtení tohoto XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> je <xref:System.Xaml.XamlReader> podtřídy.  
  
-   Výsledkem je datový proud uzlu XAML. Dostanete jednotlivé uzly použití datový proud uzlu XAML <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> rozhraní API. Nejobvyklejším operaci je posunut prostřednictvím datový proud uzlu XAML zpracování každý uzel pomocí "aktuální záznam" jedná.  
  
-   Předat výsledné uzly z na datový proud uzlu XAML <xref:System.Xaml.XamlObjectWriter> rozhraní API. <xref:System.Xaml.XamlObjectWriter> je <xref:System.Xaml.XamlWriter> podtřídy.  
  
-   <xref:System.Xaml.XamlObjectWriter> Zapíše grafu objektu, jeden objekt současně, v souladu pokroku prostřednictvím zdrojový datový proud uzlu XAML. To lze provést pomocí pomoc kontext schématu XAML a implementace, která mají přístup k sestavení a typy systém typů zálohování a framework.  
  
-   Volání <xref:System.Xaml.XamlObjectWriter.Result%2A> na konci datový proud uzlu XAML získat kořenový objekt objekt grafu.  
  
 Nejběžnější typ cestu uložení lze popsat následujícím způsobem:  
  
-   Začněte grafu objektu čas celou aplikaci spustit, obsah uživatelského rozhraní a stav doba běhu nebo menší segment reprezentace objektu celkové aplikace za běhu.  
  
-   Objekt logické spuštění, například kořenový adresář aplikace nebo kořen dokumentu zatížení objektů do <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> je <xref:System.Xaml.XamlReader> podtřídy.  
  
-   Výsledkem je datový proud uzlu XAML. Dostanete jednotlivé uzly použití datový proud uzlu XAML <xref:System.Xaml.XamlObjectReader> a <xref:System.Xaml.XamlReader> rozhraní API. Nejobvyklejším operaci je posunut prostřednictvím datový proud uzlu XAML zpracování každý uzel pomocí "aktuální záznam" jedná.  
  
-   Předat výsledné uzly z na datový proud uzlu XAML <xref:System.Xaml.XamlXmlWriter> rozhraní API. <xref:System.Xaml.XamlXmlWriter> je <xref:System.Xaml.XamlWriter> podtřídy.  
  
-   <xref:System.Xaml.XamlXmlWriter> Zápisů XAML v UTF XML kódování. To můžete uložit jako textový soubor, jako datový proud, nebo v jiných formulářů.  
  
-   Volání <xref:System.Xaml.XamlXmlWriter.Flush%2A> získat finální výstup.  
  
 Další informace o konceptech datový proud uzlu XAML najdete v tématu [struktury datový proud uzlu XAML principy a koncepty](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>XamlServices – třída  
 Není vždy nutné zabývat se datový proud uzlu XAML. Pokud chcete základní zatížení cestu nebo cestu uložení základní, můžete použít rozhraní API v <xref:System.Xaml.XamlServices> třídy.  
  
-   Různé signatury <xref:System.Xaml.XamlServices.Load%2A> implementovat cestu zatížení. Můžete buď načíst souboru nebo datový proud, nebo můžete načíst <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> nebo <xref:System.Xaml.XamlReader> , zabalení váš vstup XAML načtením s rozhraními API této čtečky.  
  
-   Různé signatury <xref:System.Xaml.XamlServices.Save%2A> uložení grafu objektu a vytvoření výstupu jako datový proud, soubor, nebo <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> Převede XAML pomocí propojení cestu k načtení a uložení cestu jako jednu operaci. Můžete použít různé schématu nebo jiné základní typ systému pro <xref:System.Xaml.XamlReader> a <xref:System.Xaml.XamlWriter>, který je co vliv, jak je transformovat výsledné XAML.  
  
 Další informace o tom, jak používat <xref:System.Xaml.XamlServices>, najdete v části [třída XAMLServices a základní XAML čtení nebo zápisu](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>XAML – systém typů  
 Systém typů XAML poskytuje rozhraní API, které jsou nutné pro práci s danou jednotlivých uzlu datový proud uzlu XAML.  
  
 <xref:System.Xaml.XamlType> Co jsou zpracování mezi počáteční objekt uzel a end objektu uzlu je reprezentace objektu.  
  
 <xref:System.Xaml.XamlMember> Co jsou zpracování mezi počáteční člen uzel a end člen uzlu je reprezentace objektu - člena.  
  
 Rozhraní API jako třeba <xref:System.Xaml.XamlType.GetAllMembers%2A> a <xref:System.Xaml.XamlType.GetMember%2A> a <xref:System.Xaml.XamlMember.DeclaringType%2A> sestavy vztahy mezi <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>.  
  
 Výchozí chování systém typů XAML, jak je implementované rozhraní .NET Framework XAML Services je na základě modul common language runtime (CLR) a statické analýzy CLR typů v sestaveních pomocí reflexe. Proto pro konkrétní typ CLR, výchozí implementace systému typ XAML vystavit schématu XAML typu a její členy a sestavy z hlediska systém typů XAML. V systému výchozí typ XAML koncept assignability typů je namapovaná na dědičnosti CLR a koncepty instancí, typy hodnot a tak dále jsou taky namapovaný na podpůrné chování a funkce modulu CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Referenční dokumentace pro funkce jazyka XAML  
 Pro podporu XAML, rozhraní .NET Framework XAML Services poskytuje konkrétní implementaci koncepty jazyka XAML, jak jsou definovány pro obor názvů jazyka XAML XAML. Ty jsou popsány jako odkaz na konkrétní stránky. Z hlediska chování tyto funkce jazyka, pokud jsou zpracovány pomocí čtečky XAML nebo XAML zapisovač, který je definován pomocí rozhraní .NET Framework XAML Services jsou popsané funkce jazyka. Další informace najdete v tématu [Namespace XAML (x:) Jazykové funkce](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
