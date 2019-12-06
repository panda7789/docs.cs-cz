---
title: Přehled převaděčů typů pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: 65210d8224b145ab23c7bc9ed76997c0892a5f59
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837256"
---
# <a name="type-converters-for-xaml-overview"></a>Přehled převaděčů typů pro jazyk XAML
Převaděče typů poskytují logiku pro zapisovač objektů, který se převede z řetězce v kódu XAML na konkrétní objekty v grafu objektů. V .NET Framework služby XAML musí být konvertor typu třída, která je odvozena od <xref:System.ComponentModel.TypeConverter>. Některé převaděče také podporují cestu pro uložení XAML a lze je použít k serializaci objektu do řetězcové notace v kódu serializace. Toto téma popisuje, jak a kdy jsou vyvolány převaděče typu v jazyce XAML, a poskytuje rady pro implementaci pro přepsání metody <xref:System.ComponentModel.TypeConverter>.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Koncepce převodu typů  
 Následující části vysvětlují základní pojmy týkající se použití řetězců a způsobu, jakým autoři objektů v .NET Framework XAML Services používají konvertory typů pro zpracování některých hodnot řetězce, které jsou zjištěny ve zdroji XAML.  
  
### <a name="xaml-and-string-values"></a>Hodnoty XAML a řetězce  
 Při nastavení hodnoty atributu v souboru XAML je počáteční typ této hodnoty řetězcem v obecném smyslu a hodnotou atributu řetězce v smyslech XML. Dokonce i jiné primitivní typy, jako je <xref:System.Double>, jsou zpočátku řetězce na procesor XAML.  
  
 Ve většině případů procesor jazyka XAML potřebuje dvě části informací pro zpracování hodnoty atributu. První část informací je typ hodnoty vlastnosti, kterou chcete nastavit. Libovolný řetězec, který definuje hodnotu atributu a který je zpracován v jazyce XAML, musí být nakonec převeden nebo přeložen na hodnotu tohoto typu. Pokud je hodnota primitivní, kterou považuje analyzátor XAML (jako je číselná hodnota), je proveden přímý převod řetězce. Pokud hodnota atributu odkazuje na výčet, je zadaný řetězec zkontrolován, že se název shoduje s pojmenovanou konstantou v tomto výčtu. Pokud hodnota není primitivní nebo konstantním názvem z výčtu, příslušný typ musí být schopný poskytnout hodnotu nebo odkaz, který je založen na převedeném řetězci.  
  
> [!NOTE]
> Direktivy jazyka XAML nepoužívají konvertory typů.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Použití rozšíření značek musí být zpracováno procesorem XAML předtím, než bude kontrolovat typ vlastnosti a další okolnosti. Například pokud vlastnost, která je nastavena jako atribut, má obvykle převod typu, ale v konkrétním případě je nastavena pomocí rozšíření značek, pak chování rozšíření označení nejprve zpracuje. Jednou z běžných situací, kdy je nutné rozšíření značek, je vytvořit odkaz na objekt, který již existuje. V tomto scénáři konvertor bezstavového typu může vytvořit pouze novou instanci, která nemusí být žádoucí. Další informace o rozšíření značek naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Převaděče nativního typu  
 V implementacích služeb WPF a .NET XAML jsou některé typy CLR, které mají zpracování převodu nativního typu, ale tyto typy CLR nejsou bez konvence považovány za primitivní. Příklad takového typu je <xref:System.DateTime>. Jedním z důvodů je, jak funguje architektura .NET Framework: typ <xref:System.DateTime> je definován v knihovně Mscorlib, nejvíce základní knihovna v rozhraní .NET. u <xref:System.DateTime> není povolen atribut s atributem, který pochází z jiného sestavení, které zavádí závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému); Proto nemusíte podporovat běžný mechanismus zjišťování konvertoru typů. Místo toho má analyzátor XAML seznam typů, které vyžadují nativní zpracování, a zpracovává tyto typy podobně, jako jsou zpracovávány skutečné primitivy. V případě <xref:System.DateTime>zahrnuje toto zpracování volání <xref:System.DateTime.Parse%2A>.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace konvertoru typu  
 Následující části popisují rozhraní API třídy <xref:System.ComponentModel.TypeConverter>.  
  
### <a name="typeconverter"></a>TypeConverter  
 V části .NET Framework služby XAML jsou všechny převaděče typu používané pro účely XAML třídy odvozené od <xref:System.ComponentModel.TypeConverter>základní třídy. <xref:System.ComponentModel.TypeConverter> třída existovala ve verzích .NET Framework před tím, než XAML existovala; jedním z původních scénářů <xref:System.ComponentModel.TypeConverter> bylo poskytnout převod řetězce pro editory vlastností v vizuálních návrhářích.  
  
 Pro XAML je role <xref:System.ComponentModel.TypeConverter> rozbalená. Pro účely XAML je <xref:System.ComponentModel.TypeConverter> základní třídou pro poskytování podpory pro určité řetězce a převody řetězců. Z-String umožňuje analyzovat hodnotu řetězcového atributu z XAML. Do řetězce lze povolit zpracování hodnoty za běhu konkrétní vlastnosti objektu zpět do atributu v jazyce XAML pro serializaci.  
  
 <xref:System.ComponentModel.TypeConverter> definuje čtyři členy, které jsou relevantní pro převod na řetězec a z-String pro účely zpracování XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z těchto členů je nejdůležitější metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>, která převede vstupní řetězec na požadovaný typ objektu. Metodu <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> lze implementovat pro převod širšího rozsahu typů na zamýšlený cílový typ převaděče. Proto může obsluhovat účely, které přesahují jazyk XAML, jako jsou například podpůrné převody za běhu. Nicméně pro použití v jazyce XAML je důležité pouze cestu kódu, která může zpracovat <xref:System.String> vstup.  
  
 Druhá nejdůležitější metoda je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud je aplikace převedena na reprezentace kódu (například pokud je uložena do souboru XAML jako soubor), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> je zahrnuta ve větším scénáři zapisovače textu jazyka XAML, který vytváří reprezentace kódu. V tomto případě je důležité cesta kódu pro XAML, když volající předává `destinationType` <xref:System.String>.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou metody podpory, které se používají, když se služba dotazuje na možnosti implementace <xref:System.ComponentModel.TypeConverter>. Tyto metody je nutné implementovat pro návrat `true` pro případy specifické pro typ, které odpovídají metody převodu vašeho převaděče. Pro účely XAML to obecně znamená <xref:System.String> typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděče typů pro jazyk XAML  
 Každá implementace <xref:System.ComponentModel.TypeConverter> může jednoznačně interpretovat, co je platný řetězec pro převod, a může také použít nebo ignorovat popis typu, který je předán jako parametr. Důležitým aspektem konverze typu kultura a XAML je následující: i když použití lokalizovatelných řetězců jako hodnot atributů je v jazyce XAML podporováno, nelze použít tyto lokalizovatelné řetězce jako vstup konvertoru typu s konkrétními požadavky na jazykovou verzi. Toto omezení je způsobeno tím, že převaděče typů pro hodnoty atributů XAML zahrnují chování zpracování XAML ve fixním jazyce, které používá `en-US` jazykové verzi. Další informace o důvodech návrhu pro toto omezení naleznete v tématu Specifikace jazyka XAML ([\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))) nebo [globalizace a lokalizace WPF](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Jako příklad, kdy může být jazyková verze příčinou problému, některé jazykové verze používají čárku namísto tečky jako oddělovač desetinných míst pro čísla ve formě řetězce. Toto použití koliduje s chováním, které má mnoho existujících převaděčů typů, což je použití čárky jako oddělovače. Předání jazykové verze prostřednictvím `xml:lang` ve okolním kódu XAML problém nevyřeší.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Aby bylo možné použít <xref:System.ComponentModel.TypeConverter> implementaci, která podporuje XAML, musí <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metoda pro tento konvertor přijmout řetězec jako parametr `value`. Pokud je řetězec v platném formátu a lze jej převést pomocí <xref:System.ComponentModel.TypeConverter> implementace, vrácený objekt musí podporovat přetypování na typ, který je očekáván vlastností. V opačném případě musí implementace <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> vracet `null`.  
  
 Každá implementace <xref:System.ComponentModel.TypeConverter> může jednoznačně interpretovat, co představuje platný řetězec pro převod, a může také použít nebo ignorovat popis typu nebo kontexty jazykové verze, které jsou předány jako parametry. Zpracování XAML jazyka WPF však nemusí předat hodnoty do kontextu popisu typu ve všech případech a také nemusí předávat kulturu na základě `xml:lang`.  
  
> [!NOTE]
> Nepoužívejte složené závorky ({}), konkrétně levou složenou závorku ({), jako prvek formátu řetězce. Tyto znaky jsou vyhrazené jako vstupní a výstupní sekvence pro rozšíření kódu.  
  
 Je vhodné vyvolat výjimku, pokud váš konvertor typu musí mít přístup ke službě XAML z modulu .NET Framework modul pro zápis objektů XAML Services, ale volání <xref:System.IServiceProvider.GetService%2A>, které je provedeno proti kontextu, nevrátí tuto službu.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> se potenciálně používá pro podporu serializace. Podpora serializace prostřednictvím <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro váš vlastní typ a konvertor typu není absolutní požadavek. Nicméně pokud implementujete ovládací prvek nebo použijete serializaci jako součást funkcí nebo návrh vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby bylo možné použít <xref:System.ComponentModel.TypeConverter> implementaci podporující jazyk XAML, musí metoda <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro tento konvertor přijmout instanci typu (nebo hodnotu), která je podporována jako parametr `value`. Pokud je parametr `destinationType` typu <xref:System.String>, vrácený objekt musí být schopný přetypovat jako <xref:System.String>. Vrácený řetězec musí představovat serializovanou hodnotu `value`. V ideálním případě by měl mít formát serializace možnost generovat stejnou hodnotu, jako kdyby byl tento řetězec předán do <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementace stejného převaděče bez významné ztráty informací.  
  
 Pokud hodnotu nelze serializovat nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementace musí vracet `null` a může vyvolat výjimku. Nicméně pokud vyvoláte výjimky, měli byste ohlásit neschopnost použít tento převod jako součást implementace <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> tak, aby se v souladu s osvědčenými postupy kontroly <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> nejprve zabránilo výjimkám.  
  
 Pokud parametr `destinationType` není typu <xref:System.String>, můžete zvolit vlastní zpracování převaděče. Obvykle se vrátíte zpět k základnímu zpracování implementace, které v základní <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolá konkrétní výjimku.  
  
 Je vhodné vyvolat výjimku, pokud váš konvertor typu musí mít přístup ke službě XAML z modulu .NET Framework modul pro zápis objektů XAML Services, ale volání <xref:System.IServiceProvider.GetService%2A>, které je provedeno proti kontextu, nevrátí tuto službu.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše implementace <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by měla vracet `true` pro `sourceType` typu <xref:System.String> a jinak, podložit základní implementaci. Nevyvolávat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše implementace <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by měla vracet `true` pro `destinationType` typu <xref:System.String>a jinak podložit základní implementaci. Nevyvolávat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Pro vlastní konvertor typu, který se má použít jako převaděč jako typ pro vlastní třídu .NET Framework XAML Services, je nutné použít <xref:System.ComponentModel.TypeConverterAttribute> na definici vaší třídy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A>, které zadáte prostřednictvím atributu, musí být název typu vašeho převaděče vlastního typu. Použijete-li tento atribut, pokud procesor XAML zpracuje hodnoty, kde typ vlastnosti používá vlastní typ třídy, může vstupní řetězce a vracet instance objektů.  
  
 Můžete také zadat konvertor typu na základě jednotlivých vlastností. Namísto použití <xref:System.ComponentModel.TypeConverterAttribute> pro definici třídy, použijte ji pro definici vlastnosti (hlavní definice, nikoli `get`/`set` implementacemi v rámci IT). Typ vlastnosti se musí shodovat s typem, který je zpracován vaším vlastním převaděčem typu. Při použití tohoto atributu, pokud procesor XAML zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vracet instance objektů. Technika konvertoru typu pro jednotlivé vlastnosti je obzvláště užitečná, pokud se rozhodnete použít typ vlastnosti z Microsoft .NET Framework nebo z jiné knihovny, kde nemůžete určit definici třídy a nelze použít <xref:System.ComponentModel.TypeConverterAttribute>.  
  
 Chcete-li zadat chování převodu typu pro vlastního připojeného člena, použijte <xref:System.ComponentModel.TypeConverterAttribute> k metodě přístupového objektu `Get` vzoru implementace pro připojeného člena.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontextu poskytovatele služby z implementace rozšíření značek  
 Dostupné služby jsou pro libovolný převaděč hodnot stejné. Rozdíl je v tom, jak každý konvertor hodnot přijímá kontext služby. Přístup ke službám a službám, které jsou k dispozici, jsou popsány v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlu XAML  
 Pokud pracujete s datovým proudem uzlu XAML, není dosud provedena akce nebo konečný výsledek převaděče typu. V cestě zatížení je řetězec atributu, který je nakonec nutné převést na typ, aby se načetl jako textová hodnota v rámci počátečního a koncového člena. Konvertor typu, který je nakonec potřebný pro tuto operaci, lze určit pomocí vlastnosti <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType>. Získání platné hodnoty z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> však spoléhá na použití kontextu schématu XAML, který může přistupovat k takovým informacím prostřednictvím podkladového člena, nebo typu hodnoty objektu, kterou člen používá. Vyvolání chování převodu typu také vyžaduje kontext schématu XAML, protože to vyžaduje mapování typů a vytvoření instance převaděče.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Přehled XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
