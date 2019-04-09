---
title: Přehled převaděčů typů pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 7a5ec731eacda8017c307a0ffa8ec282da78c40f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095721"
---
# <a name="type-converters-for-xaml-overview"></a>Přehled převaděčů typů pro jazyk XAML
Typ převaděče dodavatelského logiku pro objekt zapisovače, který převede z řetězce v kódu XAML na konkrétní objekty v grafu objektů. V rozhraní .NET Framework XAML Services musí být převaděč typu třída, která je odvozena z <xref:System.ComponentModel.TypeConverter>. Některé převaděče také podporují XAML cesta pro uložení a je možné serializovat objekt do formátu řetězce v kódu serializace. Toto téma popisuje, jak a kdy jsou vyvolány převaděče typů v XAML a obsahuje implementace doporučení pro metody přepsání <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Typ převodu koncepty  
 Následující části popisují základní koncepty o používání řetězců v XAML a o objektu zapisovače v rozhraní .NET Framework XAML Services použití převaděče typů pro zpracování některých z řetězcové hodnoty, které se vyskytují ve zdroji XAML.  
  
### <a name="xaml-and-string-values"></a>XAML a hodnotami řetězců  
 Když nastavíte hodnotu atributu v souboru XAML, počáteční typ tato hodnota je řetězec v obecném smyslu a řetězcovou hodnotu atributu ve smyslu XML. Dokonce i v dalších primitivních elementů, jako <xref:System.Double> jsou zpočátku řetězců, které mají procesor XAML.  
  
 Ve většině případů musí procesor XAML dva druhy údajů zpracovat hodnotu atributu. První část informací je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který, jsou zpracovávána v XAML musí být nakonec převést nebo přeložit hodnotu daného typu. Pokud je hodnota jednoduchého typu, který je srozumitelné pro analyzátor XAML (například číselná hodnota), dojde k pokusu o přímý převod řetězce. Pokud hodnota pro atribut odkazuje na výčet, zadaný řetězec je zaškrtnuté políčko pro porovnání název pojmenované konstanty tohoto výčtu. Pokud hodnota není na primitivní analyzátor rozumí ani názvem konstanty z výčtu, musí být schopný poskytnout hodnoty nebo odkazu, který je založen na převedený řetězec příslušného typu.  
  
> [!NOTE]
>  Direktivy jazyka XAML nepoužívejte typ převaděče.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Použití rozšíření značky musí být zpracován procesorem XAML zkontroluje pro typ vlastnosti a další důležité informace. Například pokud je vlastnost nastavena jako atribut obvykle obsahuje převod typu, ale v konkrétním případě podle použití rozšíření značky, chování rozšíření značek zpracuje první. Jedna běžné situace, kde je nutné rozšíření značek, je vytvořit odkaz na objekt, který již existuje. V tomto scénáři bezstavový typ převaděče generovat jenom nové instance, který nemusí být žádoucí. Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek XAML přehled](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Nativní typ převaděče  
 Implementace služby WPF a .NET XAML existují určité typy CLR, které mají nativní typ převodu zpracování, ale tyto typy CLR nejsou představit konvenčně primitivní. Příklad takového typu je <xref:System.DateTime>. Jedním z důvodů je, jak funguje architektury .NET Framework: typ <xref:System.DateTime> je definována v mscorlib, většina základních knihoven v .NET. <xref:System.DateTime> není dovoleno přiřadit atributem, který pochází z jiného sestavení, který vytvoří závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému), proto nelze podporovat mechanismu obvykle typ převaděče zjišťování přidělování. Místo toho analyzátoru XAML obsahuje seznam typů, které je třeba nativní zpracování a zpracování těchto typů podobný zpracování true primitiv. V případě třídy <xref:System.DateTime>, toto zpracování zahrnuje volání <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace konvertor typu  
 Následující části popisují rozhraní API se <xref:System.ComponentModel.TypeConverter> třídy.  
  
### <a name="typeconverter"></a>TypeConverter  
 V rozhraní .NET Framework XAML Services všechny převaděče typů, které se používají pro účely XAML jsou třídy, které jsou odvozeny od základní třídy <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Třídy existovaly ve verzích rozhraní .NET Framework před XAML existoval; jeden z původní <xref:System.ComponentModel.TypeConverter> scénáře bylo převodu řetězce pro vlastnost editory ve vizuální návrhářské nástroje.  
  
 Pro XAML, role <xref:System.ComponentModel.TypeConverter> rozbalen. Pro účely XAML <xref:System.ComponentModel.TypeConverter> je základní třídou pro poskytování podpory pro řetězec určité a převody z řetězce. Z řetězce umožňuje analýzu řetězcovou hodnotu atributu z XAML. Pro řetězec může povolit zpracování za běhu hodnotu vlastnosti konkrétního objektu zpět do atributu v XAML pro serializaci.  
  
 <xref:System.ComponentModel.TypeConverter> definuje čtyři členy, které jsou relevantní pro převod na řetězec a z řetězce pro účely zpracování XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z těchto členů je nejdůležitější způsob <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, který převede vstupní řetězec na typ požadovaný objekt. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Metoda opatření jsou potřebná k používání nástroje většímu počtu typů převést na zamýšlený cílový typ převaděče. Proto může posloužit účely, které přesahují XAML, jako je například podpory převodů za běhu. Ale pro použití XAML, pouze do cesty kódu, která dokáže zpracovávat <xref:System.String> vstup je důležité.  
  
 Druhá nejdůležitější způsob je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud je k reprezentaci značky (například, pokud je uložen jako soubor XAML), převést aplikace <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> je součástí větší scénář vytvoření zapisovače textu XAML reprezentaci značky. V tomto případě je důležité kód cestu pro XAML při volající předává `destinationType` z <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou metody podpory, které se používají, když služba dotazuje možnosti <xref:System.ComponentModel.TypeConverter> implementace. Je nutné implementovat tyto metody k vrácení `true` pro konkrétní typ, který odpovídá převod metody vaše konvertoru podporují. Pro účely XAML to obvykle znamená, <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděčů typů pro XAML  
 Každý <xref:System.ComponentModel.TypeConverter> implementace jednoznačně interpretovat, co je platný řetězec pro převod a můžete také použít nebo ignorovat popis typu, který je předán jako parametry. Což je důležité pro převod typu jazykovou verzi a XAML je následující: i když lokalizovatelných řetězců pomocí jako hodnoty atributů je podporovaná XAML, nelze použít tyto lokalizovatelných řetězců jako vstupní typ převaděče s požadavky na konkrétní jazykové verze. Toto omezení je, protože typ převaděče hodnot atributů XAML zahrnují chování nutně oprava jazyka XAML zpracování, které používá `en-US` jazykovou verzi. Další informace o návrhu důvody pro toto omezení, naleznete v tématu Specifikace jazyka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) nebo [WPF přehled globalizace a lokalizace](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Jako příklad, kde jazykovou verzi může být problém některých jazykových verzí čárku místo použít tečku jako oddělovač desetinné čárky pro čísla ve formátu řetězce. Toto použití koliduje s chování, které mají mnoho existujících převaděče typů, která se má použít čárku jako oddělovač. Předání jazykovou verzi prostřednictvím `xml:lang` v okolního XAML nebyl vyřešen problém.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Má být použitelná jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metoda pro tento převodník musí přijímat jako řetězec `value` parametr. Pokud řetězec v platném formátu a lze převést pomocí <xref:System.ComponentModel.TypeConverter> implementaci vráceného objektu musí podporovat přetypování na typ, který se očekává vlastností. V opačném případě <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musí vracet implementace `null`.  
  
 Každý <xref:System.ComponentModel.TypeConverter> implementace jednoznačně interpretovat, co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat typ kontexty popis nebo jazykové verze, které jsou předány jako parametry. Ale WPF XAML zpracování nemusí předat hodnoty do kontextu popis typu ve všech případech a také nemusí předat na základě jazykové verze `xml:lang`.  
  
> [!NOTE]
>  Nepoužívejte složené závorky ({}), konkrétně levou složenou závorku ({}), jako element řetězce formátu. Tyto znaky jsou rezervované jako vstupní a výstupní pořadí rozšíření značek.  
  
 Je vhodné k vyvolání výjimky, když vaše konvertor typu musí mít přístup ke službě XAML z objektu zapisovače rozhraní .NET Framework XAML Services ale <xref:System.IServiceProvider.GetService%2A> volání, které se provádí proti kontextu nevrací danou službu.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potenciálně se používá pro podporu serializace. Podpora serializace prostřednictvím <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro vlastní typ a jeho typ převaděče není jasný požadavek. Nicméně, pokud jsou implementaci ovládacího prvku, nebo pomocí serializace jako součást funkcí nebo návrhu vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Má být použitelná jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody pro tento převodník musí přijmout instance typu (nebo hodnotu), který je podporovaný jako `value` parametru. Když `destinationType` je parametr typu <xref:System.String>, vrácený objekt musí být schopné provést přetypování jako <xref:System.String>. Vrácený řetězec musí představovat serializovaná hodnota `value`. V ideálním případě by měli být schopni generovat stejnou hodnotu jako by byly předány tento řetězec formátu serializace, který zvolíte <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementace konvertoru stejné bez výrazné ztráty informací.  
  
 Pokud hodnotu nelze serializovat nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musí vracet implementace `null` a může vrátit výjimku. Nicméně pokud vyvolat výjimky, ohlaste nemožnosti převodu používat jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace tak, aby osvědčený postup kontroly s <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> nejprve výjimky, aby se podporuje.  
  
 Pokud `destinationType` parametr není typu <xref:System.String>, můžete použít vlastní převodník zpracování. Obvykle můžete vrátit k základní implementace zpracování, které v základní třídě <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolá určité výjimky.  
  
 Je vhodné k vyvolání výjimky, když vaše konvertor typu musí mít přístup ke službě XAML z objektu zapisovače rozhraní .NET Framework XAML Services ale <xref:System.IServiceProvider.GetService%2A> volání, které se provádí proti kontextu nevrací danou službu.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by měla vrátit implementaci `true` pro `sourceType` typu <xref:System.String> a v opačném případě odložit na základní implementaci. Nevyvolají výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by měla vrátit implementaci `true` pro `destinationType` typu <xref:System.String>a v opačném případě odložit na základní implementaci. Nevyvolají výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Pro vaše vlastní konvertor typu pro použití jako jednající konvertor typu pro vlastní třídu v rozhraní .NET Framework XAML Services, musíte použít [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definice třídy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Určenou prostřednictvím atributu musí být název typu konvertoru vlastního typu. Pokud použijete tento atribut při XAML procesor zpracovává hodnoty, kde typ vlastnosti používá typ vaše vlastní třídy, může vstupních řetězců a vrátí instance objektů.  
  
 Můžete také zadat konvertor typu na jednotlivých vlastností. Místo použití [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definice třídy, použijte ji pro definici vlastnosti (hlavní definice není `get` / `set` implementace v rámci něj). Typ vlastnosti musí odpovídat typ, který zpracovává vaše vlastní konvertor typu. Pomocí tohoto atributu se použije když procesor XAML zpracovává hodnoty této vlastnosti, se můžou zpracovávat vstupního řetězce a vrátí instance objektů. Na vlastnost typ převaděče technika je zvlášť užitečné, pokud se rozhodnete použít typ vlastnosti z rozhraní Microsoft .NET Framework nebo z některé jiné knihovny, kde nemůžeme mít pod kontrolou definice třídy a nejde použít <xref:System.ComponentModel.TypeConverterAttribute> existuje.  
  
 Chcete-li zadat vlastní připojené člena chování převodu typu, použijte <xref:System.ComponentModel.TypeConverterAttribute> k `Get` přístupové metody pro připojené člena implementaci vzoru.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontext zprostředkovatele služby z implementace rozšíření značek  
 Dostupné služby jsou stejné pro všechny převaděč hodnoty. Rozdíl je v jak každý převaděč hodnoty obdrží kontext služby. Přístup k službám a službám, které jsou k dispozici jsou popsány v tématu [převaděče typů a rozšíření značek pro XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v Stream uzlu XAML  
 Pokud pracujete s datový proud uzlu XAML, není dosud spuštění akce nebo konečný výsledek konvertor typu. V cestě zatížení zůstane atribut řetězec, který nakonec musí být typ převést, aby bylo možné načíst jako textové hodnoty uvnitř člen start a end – člen. Převaděč typu, který se nakonec potřebná pro tuto operaci můžete určit pomocí <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> vlastnost. Však získat platnou hodnotu z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> spoléhá na s kontext schématu XAML, který má přístup k takové informace prostřednictvím základní člen nebo typ objektu hodnoty, který používá člen. Vyvolání chování převodu typu také vyžaduje kontext schématu XAML, protože, která vyžaduje mapování typu a vytvoření instance převaděče.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
