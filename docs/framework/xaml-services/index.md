---
title: XAML Services
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 8e1e8dc9a1410d05c19e4dd1bccb30c65d7c5e66
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837282"
---
# <a name="xaml-services"></a>XAML Services
Toto téma popisuje možnosti sady technologií označované jako .NET Framework služby XAML. Většina popsaných služeb a rozhraní API se nachází v sestavení System. XAML, což je sestavení zavedené s .NET Framework 4 sadou sestavení .NET Core. Mezi služby patří čtečky a zapisovače, třídy schématu a podpora schématu, továrny, připisujících třídy, funkce vnitřní podpory jazyka XAML a další funkce jazyka XAML.  
  
## <a name="about-this-documentation"></a>O této dokumentaci  
 V Koncepční dokumentaci pro .NET Framework XAML Services se předpokládá, že máte k dispozici předchozí zkušenosti s jazykem XAML a jak se může vztahovat na konkrétní rozhraní, například [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] nebo programovací model Windows Workflow Foundation nebo v konkrétní oblasti technologie, jako je například funkce vlastního nastavení sestavení v <xref:Microsoft.Build.Framework.XamlTypes>. Tato dokumentace se nepokusí vysvětlit základy jazyka XAML jako jazyk značky, terminologie syntaxe jazyka XAML nebo jiné úvodní materiály. Místo toho se tato dokumentace zaměřuje konkrétně na použití služeb .NET Framework XAML, které jsou povoleny v knihovně sestavení System. XAML. Většina těchto rozhraní API je pro scénáře integrace a rozšiřitelnosti jazyka XAML. To může zahrnovat následující:  
  
- Rozšíření schopností základních čtecích zařízení XAML nebo zapisovačů XAML (zpracování datového proudu uzlu XAML přímo; odvození vlastního čtecího modulu XAML nebo zapisovače XAML).  
  
- Definování vlastních typů použitelných v jazyce XAML, které nemají konkrétní závislosti rozhraní, a určení typů pro předávání charakteristik systému typu XAML pro .NET Framework služby XAML.  
  
- Hostování čteček XAML nebo zapisovačů XAML jako komponenty aplikace, jako je vizuální Návrhář nebo interaktivní editor pro zdroje kódu XAML.  
  
- Zápis převaděčů hodnot XAML (rozšíření značek, převaděče typů pro vlastní typy).  
  
- Definování vlastního kontextu schématu XAML (pomocí alternativních technik načítání sestavení pro zdroje typu zálohování; použití technik vyhledávání známých typů namísto vždy odrážet sestavení; použití načtených konceptů sestavení, které nepoužívají `AppDomain` CLR a jeho přidruženého modelu zabezpečení).  
  
- Rozšíření systému základního typu XAML.  
  
- Použití technik `Lookup` nebo `Invoker` pro ovlivnění systému typů XAML a způsobu vyhodnocení zpětného navrácení.  
  
 Pokud hledáte úvodní materiál v jazyce XAML jako jazyk, můžete vyzkoušet [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md). Toto téma popisuje XAML pro cílovou skupinu, která je novinkou pro [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a také pro použití značek XAML a funkcí jazyka XAML. Dalším užitečným dokumentem je úvodní materiál ve [specifikaci jazyka XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET Framework služby XAML a System. XAML v architektuře .NET  
 V předchozích verzích Microsoft .NET Framework byla podpora pro funkce jazyka XAML implementovaná rozhraními, která jsou založená na Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], programovací model Windows Workflow Foundation a Windows Communication Foundation (WCF)), a proto se v jejich chování a v závislosti na tom, která konkrétní architektura používala, liší v chování a rozhraní API. To zahrnuje analyzátor XAML a jeho mechanismus pro vytváření grafů objektů, vnitřní prvky jazyka XAML, podporu serializace atd.  
  
 V .NET Framework 4 .NET Framework služba XAML a sestavení System. XAML definují většinu toho, co je potřeba pro podporu funkcí jazyka XAML. To zahrnuje základní třídy pro čtečky XAML a moduly pro zápis XAML. Nejdůležitější funkce přidaná do .NET Framework služby XAML, které nebyly přítomny v žádném z implementací XAML rozhraní, je typ reprezentace systému pro XAML. Reprezentace typu systému prezentuje XAML v objektově orientovaném způsobu, který vycentruje možnosti XAML, aniž by museli přebírat závislosti na konkrétních schopnostech rozhraní.  
  
 Systém typů XAML není omezen formulářem označení nebo specifickými pro modul XAML původ; ani se neomezí na konkrétní systém back-Type. Systém typů XAML zahrnuje reprezentace objektů pro typy, členy, kontexty schématu XAML, koncepty na úrovni XML a další koncepty jazyka XAML nebo vnitřní objekty XAML. Použití nebo rozšíření systému typů XAML umožňuje odvodit z tříd, jako jsou čtečky XAML a zapisovače XAML, a rozšířit funkčnost reprezentace XAML na konkrétní funkce povolené rozhraním, technologií nebo aplikací, které spotřebovávají nebo generuje XAML. Koncept kontextu schématu XAML umožňuje provádět operace zápisu do objektového grafu v rámci kombinace implementace zapisovače objektu XAML, systému typu technologie pro systém, který komunikuje prostřednictvím informací o sestavení v kontextu, a uzlu XAML. Zdrojová. Další informace o konceptu schématu XAML. viz [výchozí kontext schématu XAML a kontext WPF schématu XAML](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Streamy uzlu XAML, čtečky XAML a zapisovače XAML  
 Pro pochopení role, kterou .NET Framework XAML Services hraje v relaci mezi jazykem XAML a konkrétními technologiemi, které používají XAML jako jazyk, je užitečné pochopit koncept datového proudu uzlu XAML a způsob, jakým tento pojem tvaruje rozhraní API a vede. Datový proud uzlu XAML je koncepční přechod mezi reprezentací jazyka XAML a grafem objektu, který jazyk XAML představuje nebo definuje.  
  
- Čtečka XAML je entita, která zpracovává XAML v některém formuláři a vytváří datový proud uzlu XAML. V rozhraní API je čtečka XAML reprezentovaná <xref:System.Xaml.XamlReader>základní třídy.  
  
- Zapisovač XAML je entita, která zpracovává datový proud uzlu XAML a vytváří něco jiného. V rozhraní API je zapisovač XAML reprezentován <xref:System.Xaml.XamlWriter>základní třídy.  
  
 Dva nejběžnější scénáře týkající se jazyka XAML jsou načítány XAML pro vytvoření instance grafu objektu a uložení grafu objektů z aplikace nebo nástroje a vytváření reprezentace XAML (obvykle ve formě označení uložené jako textový soubor). Načítání kódu XAML a vytváření grafu objektů je často označováno v této dokumentaci jako cesta zatížení. Uložení nebo serializace existujícího grafu objektů do jazyka XAML je často označována v této dokumentaci jako cesta pro uložení.  
  
 Nejběžnější typ cesty načtení lze popsat následujícím způsobem:  
  
- Začněte s vyjádřením XAML ve formátu XML kódovaném ve formátu UTF a uložený jako textový soubor.  
  
- Načte tento XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> je podtřídou <xref:System.Xaml.XamlReader>.  
  
- Výsledkem je datový proud uzlu XAML. K jednotlivým uzlům datového proudu uzlu XAML můžete přistupovat pomocí <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> API. Nejběžnější operace je zde pokračovat v rámci datového proudu uzlu XAML, zpracování jednotlivých uzlů pomocí "aktuálního záznamu" metafora.  
  
- Předejte výsledné uzly z datového proudu uzlu XAML do rozhraní <xref:System.Xaml.XamlObjectWriter> API. <xref:System.Xaml.XamlObjectWriter> je podtřídou <xref:System.Xaml.XamlWriter>.  
  
- <xref:System.Xaml.XamlObjectWriter> zapisuje graf objektů, jeden objekt v čase v souladu s průběhem zdrojového datového proudu uzlu XAML. To se provádí s asistencí kontextu schématu XAML a implementací, která má přístup k sestavením a typům systému back-Type a architektury.  
  
- Volání <xref:System.Xaml.XamlObjectWriter.Result%2A> na konci datového proudu uzlu XAML pro získání kořenového objektu grafu objektu.  
  
 Nejběžnější typ cesty pro uložení lze popsat následujícím způsobem:  
  
- Začněte s grafem objektů celé doby běhu aplikace, obsahem uživatelského rozhraní a stavem doby běhu nebo menším segmentem reprezentace objektu celkové aplikace v době běhu.  
  
- Z logického spouštěcího objektu, jako je například kořen aplikace nebo kořen dokumentu, načtěte objekty do <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> je podtřídou <xref:System.Xaml.XamlReader>.  
  
- Výsledkem je datový proud uzlu XAML. K jednotlivým uzlům datového proudu uzlu XAML můžete přistupovat pomocí <xref:System.Xaml.XamlObjectReader> a rozhraní <xref:System.Xaml.XamlReader> API. Nejběžnější operace je zde pokračovat v rámci datového proudu uzlu XAML, zpracování jednotlivých uzlů pomocí "aktuálního záznamu" metafora.  
  
- Předejte výsledné uzly z datového proudu uzlu XAML do rozhraní <xref:System.Xaml.XamlXmlWriter> API. <xref:System.Xaml.XamlXmlWriter> je podtřídou <xref:System.Xaml.XamlWriter>.  
  
- <xref:System.Xaml.XamlXmlWriter> zapisuje XAML v kódování UTF XML. Můžete ho uložit jako textový soubor, jako datový proud, nebo v jiných formulářích.  
  
- Chcete-li získat konečný výstup, zavolejte <xref:System.Xaml.XamlXmlWriter.Flush%2A>.  
  
 Další informace o konceptech streamů uzlů XAML naleznete v tématu [Principy struktur a konceptů datového proudu](understanding-xaml-node-stream-structures-and-concepts.md)uzlu XAML.  
  
### <a name="the-xamlservices-class"></a>Třída XamlServices  
 Není vždy nutné řešit datový proud uzlu XAML. Pokud chcete základní cestu načtení nebo základní cestu pro uložení, můžete použít rozhraní API ve třídě <xref:System.Xaml.XamlServices>.  
  
- Různé signatury <xref:System.Xaml.XamlServices.Load%2A> implementují cestu načtení. Můžete buď načíst soubor nebo datový proud, nebo můžete načíst <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> nebo <xref:System.Xaml.XamlReader>, které zabalí vstup XAML načtením pomocí rozhraní API tohoto čtecího modulu.  
  
- Různé podpisy <xref:System.Xaml.XamlServices.Save%2A> uloží graf objektů a vytvoří výstup jako datový proud, soubor nebo <xref:System.Xml.XmlWriter>/instanci <xref:System.IO.TextWriter>.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> převádí XAML propojením cesty načtení a cesty pro uložení jako jediné operace. Pro <xref:System.Xaml.XamlReader> a <xref:System.Xaml.XamlWriter>by se mohl použít jiný kontext schématu nebo jiný systém back-Type, což vede k ovlivnění toho, jak je výsledný kód XAML transformované.  
  
 Další informace o použití <xref:System.Xaml.XamlServices>naleznete v tématu [Třída XamlServices a Basic XAML pro čtení nebo zápis](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>Systém typů XAML  
 Systém typů XAML poskytuje rozhraní API, která jsou vyžadována pro práci s daným samostatným uzlem datového proudu uzlu XAML.  
  
 <xref:System.Xaml.XamlType> je reprezentace objektu – co se zpracovává mezi uzlem počátečního objektu a uzlem koncového objektu.  
  
 <xref:System.Xaml.XamlMember> je reprezentace člena objektu – co se zpracovává mezi počátečním členem uzlu a koncovým členem uzlu.  
  
 Rozhraní API, jako jsou <xref:System.Xaml.XamlType.GetAllMembers%2A> a <xref:System.Xaml.XamlType.GetMember%2A> a <xref:System.Xaml.XamlMember.DeclaringType%2A>, hlásí vztahy mezi <xref:System.Xaml.XamlType> a <xref:System.Xaml.XamlMember>.  
  
 Výchozí chování systému typů XAML, jak je implementováno pomocí .NET Framework služby XAML, je založeno na modulu CLR (Common Language Runtime) a statické analýze typů CLR v sestaveních pomocí reflexe. Proto pro konkrétní typ CLR může výchozí implementace systému typů XAML vystavit schéma XAML tohoto typu a jeho členů a ohlásit je v rámci systému typů XAML. Ve výchozím systému typů jazyka XAML je koncept přiřazení typů mapován na dědičnost CLR a koncepty instancí, hodnotových typů a tak dále jsou mapovány na podpůrné chování a funkce modulu CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Referenční informace o funkcích jazyka XAML  
 Pro podporu XAML poskytují .NET Framework služby XAML specifickou implementaci konceptů jazyka XAML, jak jsou definovány pro obor názvů XAML jazyka XAML. Ty jsou zdokumentovány jako konkrétní referenční stránky. Jazykové funkce jsou zdokumentovány z perspektivy způsobu, jakým se tyto funkce jazyka chovají při zpracování čtečkou XAML nebo zapisovačem XAML, který je definován pomocí .NET Framework služby XAML. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce](xaml-namespace-x-language-features.md).
