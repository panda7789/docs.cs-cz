---
title: XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 373478e8c21fca66cbfbf7a58fc7d53f65ce5d0b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195096"
---
# <a name="xaml-services"></a>XAML Services
Toto téma popisuje možnosti sady technologií označované jako rozhraní .NET Framework XAML Services. Většina služeb a rozhraní API popsané jsou umístěny v oboru názvů System.Xaml, což je sestavení představeny s nástrojem sestavení [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] sadu .NET core sestavení. Mezi tyto služby patří objekty pro vytváření čtečky a zapisovače, schéma třídy a podpora schématu, zapisujících tříd, vnitřní podporu pro jazyk XAML a dalších funkcí jazyka XAML.  
  
## <a name="about-this-documentation"></a>Informace o této dokumentaci  
 Rámcové dokumentaci pro rozhraní .NET Framework XAML Services se předpokládá, že máte předchozí zkušenosti s jazykem XAML a jak jej mohou vztahovat na určité rozhraní, například [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] nebo Windows Workflow Foundation, nebo konkrétní technologie funkce oblasti, například vlastní nastavení sestavení funkce v <xref:Microsoft.Build.Framework.XamlTypes>. Tato dokumentace nebude pokoušet o vysvětluje základy XAML jako značka jazyka, terminologie syntaxe XAML nebo další úvodní materiály. Místo toho tato dokumentace se zaměřuje na konkrétně v knihovně oboru názvů System.Xaml sestavení s využitím rozhraní .NET Framework XAML Services jsou povolené. Většina těchto rozhraní API jsou určené pro scénáře integrace jazyka XAML a rozšíření. To může zahrnovat kterýkoli z následujících:  
  
-   Rozšíření možností základní XAML čtečky nebo zapisovače XAML (zpracování datový proud uzlu XAML přímo; odvozený vlastní XAML čtečky nebo zapisovače XAML).  
  
-   Definování XAML počítačově využitelný vlastních typů, které nemají závislosti konkrétní verzi rozhraní framework a zapisujících typů k vyjádření jejich XAML zadejte vlastnosti systému pro rozhraní .NET Framework XAML Services.  
  
-   Hostování jako součást aplikace, jako je například interaktivní editor pro zdroje značky XAML a vizuálního návrháře XAML čtečky nebo zapisovače XAML.  
  
-   Zápis převaděče hodnot XAML (přípony označení; převaděčů typů pro vlastní typy).  
  
-   Definování vlastních kontext schématu XAML (použití alternativní metody načtení sestavení pro základní typ zdroje; pomocí technik vyhledávání známé typy ne vždy odráží sestavení; pomocí koncepty načtené sestavení, které nepoužívají CLR `AppDomain` a svůj model zabezpečení).  
  
-   Rozšíření základního typu systému XAML.  
  
-   Použití `Lookup` nebo `Invoker` techniky k ovlivnění XAML zadejte systém a jak se vyhodnocují typ podklady.  
  
 Pokud chcete pro úvodní materiály na XAML jako jazyk, můžete se pokusit [přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Toto téma popisuje XAML pro cílovou skupinu, která je nová, jak [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a také můžete používat značky XAML a funkce jazyka XAML. Další užitečné dokument je úvodní materiály v [specifikace jazyka XAML](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Rozhraní .NET framework XAML Services a oboru názvů System.Xaml v architektuře .NET  
 V předchozích verzích rozhraní Microsoft .NET Framework, podpora pro funkce jazyka XAML bylo implementováno rozhraní, které je založená na rozhraní Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation a Windows Communication Foundation (WCF)) a proto měnit své chování a rozhraní API použít, v závislosti na tom, jaké konkrétní verzi rozhraní framework, kterou jste používali. To zahrnuje XAML analyzátor a jeho objekt grafu vytváření mechanismus, vnitřní objekty jazyka XAML, podporu serializace a tak dále.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework XAML Services a oboru názvů System.Xaml sestavení definujte většinu toho, co je potřeba pro podporu funkcí jazyka XAML. To zahrnuje základní třídy pro XAML čtečky a zapisovače XAML. Nejdůležitější funkce přidána do rozhraní .NET Framework XAML Services, která není přítomná v některém z implementace specifické pro architekturu XAML je systém reprezentaci typu pro XAML. Reprezentaci typu systému XAML představuje objektově orientované způsobem, který centra na XAML možnosti bez nutnosti přepínat závislosti na konkrétních možnostech rozhraní.  
  
 Systém typů XAML není omezeno značky formuláře a specifika za běhu původu XAML; ani je omezená rozhraním žádné konkrétní zálohování systému typů. Systém typů XAML obsahuje reprezentaci objektu pro typy, členy, kontext schématu XAML, koncepty úrovni XML a další koncepty jazyka XAML nebo vnitřní funkce XAML. Použití nebo rozšíření typu systému XAML díky tomu je možné odvodit z třídy typu XAML čtečky a zapisovače XAML a rozšíření funkcí reprezentace XAML do konkrétní funkce povolena Architektura technologie nebo aplikaci, která využívá nebo vysílá XAML. Operace zápisu praktické objektu grafu v kombinaci XAML objekt zapisovače implementace systému typ základní technologie, jak pomocí informací o sestavení v kontextu uzlu XAML a umožňuje koncept kontext schématu XAML zdroj. Další informace o schématu koncept XAML. Zobrazit [výchozí kontext schématu XAML a kontext WPF XAML schématu](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Datové proudy uzlu XAML, XAML čtečky a zapisovače XAML  
 Chcete-li pochopit, jakou roli hraje ve vztahu mezi jazyka XAML a konkrétní technologie, které používají XAML jako jazyk rozhraní .NET Framework XAML Services, je dobré znát konceptu datový proud uzlu XAML a jak tento koncept obrazce rozhraní API a terminologie. Datový proud uzlu XAML je koncepční zprostředkující mezi reprezentace jazyka XAML a graf objektu, který představuje XAML nebo definuje.  
  
-   Čtečka XAML je entita, která zpracovává XAML v nějaké podobě a vytvoří datový proud uzlu XAML. V rozhraní API čtečku XAML představuje základní třídu <xref:System.Xaml.XamlReader>.  
  
-   Zapisovač XAML je entita, která zpracovává datový proud uzlu XAML a vytváří něco jiného. V rozhraní API, zapisovač XAML představuje základní třídu <xref:System.Xaml.XamlWriter>.  
  
 Dvě nejběžnější scénáře zahrnující XAML jsou načítání XAML pro vytvoření instance grafu objektů a ukládání grafu objektů z aplikace nebo nástroje a vytváření reprezentaci XAML (obvykle v podobě značek uložen jako textový soubor). Načítání XAML a vytvoření grafu objektu je často uvedené v této dokumentaci jako načíst cestu. Uložení nebo serializaci existující graf objektu do XAML se často označuje v této dokumentaci jako Uložit cestu.  
  
 Nejběžnějším typem načíst cestu lze popsat následujícím způsobem:  
  
-   Začněte s reprezentací XAML, ve formátu XML s kódováním UTF a uložen jako textový soubor.  
  
-   Načíst tuto XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> je <xref:System.Xaml.XamlReader> podtřídy.  
  
-   Výsledkem je datový proud uzlu XAML. Jednotlivé uzly pomocí datový proud uzlu XAML jsou přístupné <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> rozhraní API. Některé běžné operace, je postupoval datový proud uzlu XAML zpracování každého uzlu pomocí "aktuální záznam" metafora.  
  
-   Předat z datový proud uzlu XAML pro výsledný uzly <xref:System.Xaml.XamlObjectWriter> rozhraní API. <xref:System.Xaml.XamlObjectWriter> je <xref:System.Xaml.XamlWriter> podtřídy.  
  
-   <xref:System.Xaml.XamlObjectWriter> Zapíše grafu objektů, jeden objekt najednou, v souladu pokroku prostřednictvím zdrojový datový proud uzlu XAML. To se provádí za pomoci kontext schématu XAML a implementace, která může přistupovat k sestavení a typy zálohování systému typů a rozhraní framework.  
  
-   Volání <xref:System.Xaml.XamlObjectWriter.Result%2A> na konci datový proud uzlu XAML získat kořenového objektu grafu objektů.  
  
 Nejběžnější druh cesta pro uložení lze popsat následujícím způsobem:  
  
-   Začněte s graf objektu je čas spuštění celé aplikace, obsah uživatelského rozhraní a stav doba běhu nebo menší segment celkové aplikace reprezentace objektu v době běhu.  
  
-   Z objektu logické spuštění, například kořen dokumentu nebo kořenový adresář aplikace načíst objekty do <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> je <xref:System.Xaml.XamlReader> podtřídy.  
  
-   Výsledkem je datový proud uzlu XAML. Jednotlivé uzly pomocí datový proud uzlu XAML jsou přístupné <xref:System.Xaml.XamlObjectReader> a <xref:System.Xaml.XamlReader> rozhraní API. Některé běžné operace, je postupoval datový proud uzlu XAML zpracování každého uzlu pomocí "aktuální záznam" metafora.  
  
-   Předat z datový proud uzlu XAML pro výsledný uzly <xref:System.Xaml.XamlXmlWriter> rozhraní API. <xref:System.Xaml.XamlXmlWriter> je <xref:System.Xaml.XamlWriter> podtřídy.  
  
-   <xref:System.Xaml.XamlXmlWriter> Zapsalo XAML XML UTF kódování. Můžete uložit jako textový soubor jako datový proud nebo v jiných formulářů.  
  
-   Volání <xref:System.Xaml.XamlXmlWriter.Flush%2A> získat konečného výstupu.  
  
 Další informace o konceptech datový proud uzlu XAML najdete v tématu [Principy XAML Stream struktur a koncepcí uzlů](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Xamlservices – třída  
 Není vždy nutné řešit datový proud uzlu XAML. Pokud chcete základní načíst cestu nebo základní cesta pro uložení, můžete použít rozhraní API v <xref:System.Xaml.XamlServices> třídy.  
  
-   Různé podpisy <xref:System.Xaml.XamlServices.Load%2A> implementovat načíst cestu. Můžete načíst soubor nebo datový proud, nebo můžete načíst <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> nebo <xref:System.Xaml.XamlReader> , zabalit váš vstup XAML načtením této čtečky rozhraní API.  
  
-   Různé podpisy <xref:System.Xaml.XamlServices.Save%2A> uložení grafu objektů a výstup pomocí datového proudu souboru, nebo <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> Převede XAML propojením načíst cestu a uložit cestu jako jediná operace. Kontext jiné schéma nebo záložní systém typů může být využíván pro <xref:System.Xaml.XamlReader> a <xref:System.Xaml.XamlWriter>, což je, co ovlivňuje, jak transformovat výsledný XAML.  
  
 Další informace o tom, jak používat <xref:System.Xaml.XamlServices>, naleznete v tématu [třída XAMLServices a základní XAML čtení nebo zápisu](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>XAML – systém typů  
 Systém typů XAML poskytuje rozhraní API, která jsou vyžadována pro práci s danou jednotlivých uzlů z datový proud uzlu XAML.  
  
 <xref:System.Xaml.XamlType> Co jsou zpracování mezi uzel objektu počáteční a koncový uzel objektu je reprezentace objektu.  
  
 <xref:System.Xaml.XamlMember> Co jsou zpracování mezi uzlem, člen počáteční a koncový člen uzlu je reprezentace pro člena objektu.  
  
 Rozhraní API, jako <xref:System.Xaml.XamlType.GetAllMembers%2A> a <xref:System.Xaml.XamlType.GetMember%2A> a <xref:System.Xaml.XamlMember.DeclaringType%2A> sestavy vztahy mezi <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>.  
  
 Výchozí chování typu systému XAML implementovaného pomocí rozhraní .NET Framework XAML Services vychází common language runtime (CLR) a statické analýzy CLR typy v sestaveních pomocí reflexe. Proto pro konkrétní typ CLR, výchozí implementace typu systému XAML vystavit schématu XAML z tohoto typu a jeho členy a sestavy z hlediska typu systému XAML. V typu systému XAML výchozí koncept přiřaditelnosti typů je mapována na CLR dědičnosti a koncepty instancí, typy hodnot a tak dále se také namapován na podpůrné chování a funkce modulu CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Referenční informace pro funkce jazyka XAML  
 K podpoře XAML, rozhraní .NET Framework XAML Services poskytuje konkrétní implementaci konceptů jazyka XAML, jak jsou definovány pro obor názvů XAML jazyka XAML. Ty jsou popsány jako odkaz na konkrétní stránky. Jazykové funkce jsou popsány z hlediska jak tyto funkce jazyka chovat, když jsou zpracovány pomocí XAML čtečky nebo zapisovače XAML, který je definován pomocí rozhraní .NET Framework XAML Services. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
