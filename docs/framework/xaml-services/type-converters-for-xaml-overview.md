---
title: "Přehled převaděčů typů pro jazyk XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b59b88c38b6fa7f810bb3a12de09a962eb5679c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="type-converters-for-xaml-overview"></a>Přehled převaděčů typů pro jazyk XAML
Typ převaděče napájení logiku pro zápisu objektu, který převádí z řetězec v kódu XAML do konkrétní objekty v grafu objektu. V rozhraní .NET Framework XAML Services převaděč typů musí být třída odvozená z <xref:System.ComponentModel.TypeConverter>. Některé převaděče také podporují XAML cestu uložení a slouží k serializaci objektu do formátu řetězec v kódu serializace. Toto téma popisuje, jak a kdy jsou vyvolány převaděče typů v jazyce XAML a poskytuje implementace Rady pro metodu přepsání <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Koncepty převody typu  
 Následující části popisují základní koncepty o používání řetězců v jazyce XAML, a jak objekt zapisovače v rozhraní .NET Framework XAML Services pomocí převaděče typů zpracovat některé z řetězcové hodnoty, které se vyskytují ve zdroji XAML.  
  
### <a name="xaml-and-string-values"></a>XAML a hodnotami řetězců  
 Když nastavíte hodnotu atributu v souboru XAML, typ počáteční této hodnoty je řetězec v obecném smyslu a řetězcovou hodnotu atributu v smysl XML. I další primitiv jako <xref:System.Double> jsou původně řetězce pro procesor XAML.  
  
 Ve většině případů musí procesor XAML dva údaje zpracovat hodnotu atributu. První část informace je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který zpracovává v jazyce XAML musí být nakonec převést nebo byl přeložen na hodnotu daného typu. Pokud je hodnota Primitivum, které se rozumí analyzátor jazyka XAML (například číselnou hodnotu), dojde k pokusu o přímé převod řetězce. Pokud hodnotu pro atribut odkazuje na výčet, zkontroluje se zadaný řetězec pro název shodu s názvem konstanta tohoto výčtu. Pokud je hodnota jednoduchého typu rozumí analyzátor ani konstantní název z výčtu, musí být schopen poskytnout hodnotu nebo odkaz, který je založen na řetězec převedený příslušného typu.  
  
> [!NOTE]
>  Direktivy jazyka XAML nepoužívejte typ převaděče.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Použití rozšíření značek musí být zpracován procesorem XAML zkontroluje vlastnost type a další důležité informace. Například pokud je vlastnost nastavena jako atribut má obvykle převod typu, ale v konkrétním případě využitím rozšíření značek, chování rozšíření značek zpracovávání nejdřív. Jeden běžné situace, kdy je nezbytné rozšíření značek je aby odkaz na objekt, který již existuje. V tomto scénáři konvertor bezstavové typu generovat jenom novou instanci, která nemusí být žádoucí. Další informace o rozšíření značek najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Převaděče nativním typu  
 V implementacích služby WPF a .NET XAML existují určité typy CLR, které mají nativní typ převodu zpracování, ale tyto typy CLR nejsou představit obvykle jako primitivní elementy. Příkladem takového typu je <xref:System.DateTime>. Jedním z důvodů je, jak funguje Architektura rozhraní .NET Framework: typ <xref:System.DateTime> je definována v mscorlib, nejzákladnější knihovny v rozhraní .NET. <xref:System.DateTime>nemá oprávnění k být opatřená atribut, který pochází z jiného sestavení, které představuje závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému); proto nemůže být podporováno mechanismus obvyklé typ převaděče zjišťování pomocí zapisujících. Místo toho analyzátor XAML má seznam typů, které je třeba nativní zpracování a zpracování těchto typů podobná zpracování true primitiv. U <xref:System.DateTime>, zpracování zahrnuje volání <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace převaděče typů  
 Následující části popisují rozhraní API <xref:System.ComponentModel.TypeConverter> třídy.  
  
### <a name="typeconverter"></a>TypeConverter  
 V rozhraní .NET Framework XAML Services všechny převaděče typů, které se používají pro účely XAML jsou třídy, které jsou odvozeny od základní třídy <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Třída existovalo v verze rozhraní .NET Framework dříve, než XAML vznikla; jeden z původní <xref:System.ComponentModel.TypeConverter> scénáře bylo převod řetězce pro vlastnost editory v visual Designer.  
  
 Pro jazyk XAML, role <xref:System.ComponentModel.TypeConverter> je rozšířena. Pro účely XAML <xref:System.ComponentModel.TypeConverter> je základní třídou pro zajištění podpory pro řetězec určité a převody z řetězce. Z řetězce umožňuje analýzu řetězcovou hodnotu atributu z XAML. Na řetězce může povolit zpracování hodnota doby běhu vlastnosti konkrétního objektu zpět do atribut v jazyce XAML pro serializaci.  
  
 <xref:System.ComponentModel.TypeConverter>definuje čtyři členy, které jsou relevantní pro převod na řetězce a z řetězce pro účely zpracování XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Tyto členy, je nejdůležitější metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, která převede vstupní řetězec na typ požadovaný objekt. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Může být implementována metoda převést na typ určený cílový převaděč širší rozsah typy. Proto může posloužit účely, které přesahují XAML, jako je podpora převody běhu. Ale pro použití XAML, pouze kódová cesta, která může zpracovat <xref:System.String> vstup je důležité.  
  
 Je druhý nejdůležitější metoda <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud aplikace je převést na znázornění značek (například pokud je uloženo do jazyka XAML jako soubor), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> je součástí větší scénář produktů zapisovače textu XAML znázornění značek. V takovém případě je důležité kódová cesta pro jazyk XAML tehdy, když volání `destinationType` z <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> podporu metod, které se použijí při služby dotazuje možnosti <xref:System.ComponentModel.TypeConverter> implementace. Je nutné implementovat tyto metody vrátit `true` pro konkrétní typ případů, které podporují převod ekvivalentní metody vaší převaděč. Pro účely XAML to obvykle znamená <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi, převaděčů typů pro jazyk XAML  
 Každý <xref:System.ComponentModel.TypeConverter> implementace jednoznačně dokáže interpretovat, co je platný řetězec pro převod a můžete také použít nebo ignorovat popis typu, který je předán jako parametry. Důležitá poznámka pro jazykovou verzi a XAML typ – převod je následující: i když pomocí možnosti lokalizace řetězce jako hodnoty atributů je podporovaná XAML, tyto možnosti lokalizace řetězce nelze použít jako vstup převaděče typu s požadavky na konkrétní jazykové verze. Toto omezení je totiž převaděčů typů pro hodnoty atributu XAML chování nutně pevné jazyka XAML zpracování, které používá `en-US` jazykovou verzi. Další informace o návrhu důvody pro toto omezení, najdete v části specifikace jazyka XAML ([\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)) nebo [WPF globalizace a lokalizace přehled](../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Jako příklad, kdy jazykovou verzi může být problém některé jazykové verze použít čárku místo období jako oddělovač desetinných čísel ve formátu řetězce. Toto použití koliduje se chování, které mají mnoho existující převaděče typů, který má používat jako oddělovač čárkou. Předávání jazykové verze prostřednictvím `xml:lang` v okolního XAML nebyl vyřešen problém.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Možné používat jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metodu pro tento převaděč musí přijmout řetězec jako `value` parametr. Pokud řetězec v platném formátu a mohou být pomocí převedeny <xref:System.ComponentModel.TypeConverter> implementace vráceného objektu musí podporovat přetypování na typ, který je očekávaný vlastností. Jinak <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musí vracet implementace `null`.  
  
 Každý <xref:System.ComponentModel.TypeConverter> implementace jednoznačně dokáže interpretovat, co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat typ kontexty popis nebo jazykové verze, které se předávají jako parametry. Ale XAML WPF zpracování nemusí předat hodnoty do kontextu popis typu ve všech případech a nemusí předat také jazykovou verzi na základě `xml:lang`.  
  
> [!NOTE]
>  Nepoužívejte složené závorky ({}), konkrétně levá složená závorka ({}), jako element vaší formát řetězce. Tyto znaky jsou vyhrazené jako vstup a výstup pro rozšíření pořadí značek.  
  
 Je třeba způsobí výjimku, pokud vaše převaděče typů musí mít přístup k XAML služby z objektu zapisovač rozhraní .NET Framework XAML Services, ale <xref:System.IServiceProvider.GetService%2A> volání, které se provádí před kontextu nevrací dané služby.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>potenciálně se používá pro podporu serializace. Podpora serializace prostřednictvím <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro vlastní typ a jeho typ není převaděč absolutní požadavek. Ale pokud jsou implementaci ovládacího prvku, nebo pomocí serializace jako součást funkce nebo návrh vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Možné používat jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metodu pro tento převaděč musí přijmout instanci typu (nebo hodnotu), který je podporovaný jako `value` parametr. Když `destinationType` parametr je typu <xref:System.String>, vráceného objektu musí být schopen převést jako <xref:System.String>. Vrácený řetězec musí představovat serializovaná hodnota `value`. V ideálním případě by mohli vygenerovat stejnou hodnotu jako v případě, že bylo předáno tento řetězec formátu serializace, který zvolíte, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementace stejné převaděč bez významné ztrátě informací.  
  
 Pokud hodnota nemůže být serializován nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musí vracet implementace `null` a může vyvolat výjimku. Ale pokud generování výjimek, byste měli hlásit nemožnost použít tento převod jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace tak, aby osvědčený postup, kontrola s <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> nejprve vyhnout výjimky se podporuje.  
  
 Pokud `destinationType` parametr není typu <xref:System.String>, můžete zvolit vlastní převaděč zpracování. Obvykle můžete vrátit do základní implementaci zpracování, které v základní <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolá určité výjimky.  
  
 Je třeba způsobí výjimku, pokud vaše převaděče typů musí mít přístup k XAML služby z objektu zapisovač rozhraní .NET Framework XAML Services, ale <xref:System.IServiceProvider.GetService%2A> volání, které se provádí před kontextu nevrací dané služby.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by měla vrátit implementace `true` pro `sourceType` typu <xref:System.String> a, jinak hodnota odložení základní implementaci. Nevyvolá výjimku výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by měla vrátit implementace `true` pro `destinationType` typu <xref:System.String>a jinak odložení základní implementaci. Nevyvolá výjimku výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Pro vaše vlastní typ převaděče má být použit jako funguje převaděč typů pro třídu vlastní pomocí rozhraní .NET Framework XAML Services, musíte použít [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> vaše definici třídy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Zadáte prostřednictvím atributu musí být název typu vaše vlastní typ převaděče. Pokud použijete tento atribut při XAML procesor zpracovává hodnoty, kde typ vlastnosti používá typ vaše vlastní třídy, může se vstup řetězce a vrátí instance objektů.  
  
 Převaděče typů můžete zadat taky na jednotlivých vlastností. Místo použití [!INCLUDE[TLA#tla_netframewkattr](../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> v definici třídy použijte ho pro definici vlastnosti (hlavní definice není `get` / `set` implementace v něm). Typ vlastnosti musí odpovídat typ, který zpracovává vaše vlastní typ převaděče. K tomuto atributu se použije když XAML procesor zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vrátí instance objektů. Postup pro vlastnosti typu převaděč je zvláště užitečné, pokud chcete použít typ vlastnosti z [!INCLUDE[TLA#tla_netframewk](../../../includes/tlasharptla-netframewk-md.md)] nebo z některé jiné knihovny, kde nemůže ovládat definice třídy a nelze použít <xref:System.ComponentModel.TypeConverterAttribute> existuje.  
  
 Chcete-li zadat typ převodu chování vlastní připojené člena, použít <xref:System.ComponentModel.TypeConverterAttribute> k `Get` metoda přistupujícího objektu implementace vzoru pro připojené člena.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontext zprostředkovatele služby z implementaci rozšíření značek  
 Služby k dispozici jsou stejné pro všechny převaděč hodnoty. Rozdíl spočívá v tom, jak každý převaděč hodnoty obdrží kontext služby. Přístup k službám a službami, které jsou k dispozici jsou popsané v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datový proud uzlu XAML  
 Pokud pracujete s datový proud uzlu XAML, není ještě spuštěna akce nebo konečný výsledek převaděče typů. V cestě zatížení zůstává řetězec atributu, který nakonec musí být typ převést, aby bylo možné načíst jako textovou hodnotu v rámci člen start a end – člen. Nakonec potřebné pro tuto operaci se dá určit pomocí převaděče typu <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> vlastnost. Však získat platnou hodnotu z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> spoléhá na nutnosti kontext schématu XAML, který má přístup k takové informace prostřednictvím základní člen nebo typ hodnota objektu, který používá člena. Vyvolání chování převodu typu také vyžaduje kontext schématu XAML, protože typ mapování, která vyžaduje a vytvoření instance převaděče.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Přehled XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
