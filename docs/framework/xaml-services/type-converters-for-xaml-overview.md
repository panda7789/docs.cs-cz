---
title: Přehled převaděčů typů pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: e401b40e1c11504e3c27d5b3601d71ef8f5821e1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169009"
---
# <a name="type-converters-for-xaml-overview"></a>Přehled převaděčů typů pro jazyk XAML
Převaděče typů poskytují logiku pro zapisovač objektů, který se převede z řetězce v kódu XAML na konkrétní objekty v grafu objektů. V .NET Framework služby XAML musí být konvertor typu třída, která je odvozena z <xref:System.ComponentModel.TypeConverter>. Některé převaděče také podporují cestu pro uložení XAML a lze je použít k serializaci objektu do řetězcové notace v kódu serializace. Toto téma popisuje, jak a kdy jsou vyvolány převaděče typu v jazyce XAML, a poskytuje rady pro <xref:System.ComponentModel.TypeConverter>implementaci pro přepsání metody.  
  
<a name="type_conversion_concepts"></a>   
## <a name="type-conversion-concepts"></a>Koncepce převodu typů  
 Následující části vysvětlují základní pojmy týkající se použití řetězců a způsobu, jakým autoři objektů v .NET Framework XAML Services používají konvertory typů pro zpracování některých hodnot řetězce, které jsou zjištěny ve zdroji XAML.  
  
### <a name="xaml-and-string-values"></a>Hodnoty XAML a řetězce  
 Při nastavení hodnoty atributu v souboru XAML je počáteční typ této hodnoty řetězcem v obecném smyslu a hodnotou atributu řetězce v smyslech XML. Dokonce i jiné primitivní prvky, <xref:System.Double> jako jsou první řetězce, na procesor XAML.  
  
 Ve většině případů procesor jazyka XAML potřebuje dvě části informací pro zpracování hodnoty atributu. První část informací je typ hodnoty vlastnosti, kterou chcete nastavit. Libovolný řetězec, který definuje hodnotu atributu a který je zpracován v jazyce XAML, musí být nakonec převeden nebo přeložen na hodnotu tohoto typu. Pokud je hodnota primitivní, kterou považuje analyzátor XAML (jako je číselná hodnota), je proveden přímý převod řetězce. Pokud hodnota atributu odkazuje na výčet, je zadaný řetězec zkontrolován, že se název shoduje s pojmenovanou konstantou v tomto výčtu. Pokud hodnota není primitivní nebo konstantním názvem z výčtu, příslušný typ musí být schopný poskytnout hodnotu nebo odkaz, který je založen na převedeném řetězci.  
  
> [!NOTE]
> Direktivy jazyka XAML nepoužívají konvertory typů.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Použití rozšíření značek musí být zpracováno procesorem XAML předtím, než bude kontrolovat typ vlastnosti a další okolnosti. Například pokud vlastnost, která je nastavena jako atribut, má obvykle převod typu, ale v konkrétním případě je nastavena pomocí rozšíření značek, pak chování rozšíření označení nejprve zpracuje. Jednou z běžných situací, kdy je nutné rozšíření značek, je vytvořit odkaz na objekt, který již existuje. V tomto scénáři konvertor bezstavového typu může vytvořit pouze novou instanci, která nemusí být žádoucí. Další informace o rozšíření značek naleznete v tématu [Přehled rozšíření značek pro jazyk XAML](markup-extensions-for-xaml-overview.md).  
  
### <a name="native-type-converters"></a>Převaděče nativního typu  
 V implementacích služeb WPF a .NET XAML jsou některé typy CLR, které mají zpracování převodu nativního typu, ale tyto typy CLR nejsou bez konvence považovány za primitivní. Příklad takového typu je <xref:System.DateTime>. Jedním z důvodů je, jak funguje architektura .NET Framework: typ <xref:System.DateTime> je definován v knihovně Mscorlib, nejvíce základní knihovna rozhraní .NET. <xref:System.DateTime>není povoleno mít atribut s atributem, který pochází z jiného sestavení, které zavádí závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému); proto není možné podporovat běžný mechanismus zjišťování konvertoru typů. Místo toho má analyzátor XAML seznam typů, které vyžadují nativní zpracování, a zpracovává tyto typy podobně, jako jsou zpracovávány skutečné primitivy. V případě <xref:System.DateTime>tohoto zpracování zahrnuje <xref:System.DateTime.Parse%2A>volání.  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace konvertoru typu  
 Následující části popisují rozhraní API <xref:System.ComponentModel.TypeConverter> třídy.  
  
### <a name="typeconverter"></a>TypeConverter  
 V části .NET Framework XAML Services jsou všechny převaděče typu, které jsou používány pro účely XAML, třídy odvozené ze základní <xref:System.ComponentModel.TypeConverter>třídy. Třída existovala ve verzích .NET Framework před tím, než XAML existovala. jedním z <xref:System.ComponentModel.TypeConverter> původních scénářů bylo poskytnout převod řetězce pro editory vlastností v vizuálních návrhářích. <xref:System.ComponentModel.TypeConverter>  
  
 Pro XAML <xref:System.ComponentModel.TypeConverter> je role rozbalená. Pro účely <xref:System.ComponentModel.TypeConverter> XAML je základní třídou pro poskytování podpory pro určité řetězce a převody řetězců. Z-String umožňuje analyzovat hodnotu řetězcového atributu z XAML. Do řetězce lze povolit zpracování hodnoty za běhu konkrétní vlastnosti objektu zpět do atributu v jazyce XAML pro serializaci.  
  
 <xref:System.ComponentModel.TypeConverter>definuje čtyři členy, které jsou relevantní pro převod na řetězec a z-String pro účely zpracování XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z těchto členů je <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>nejdůležitější metodou, která převede vstupní řetězec na požadovaný typ objektu. <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> Metoda může být implementována pro převod širšího rozsahu typů na zamýšlený cílový typ převaděče. Proto může obsluhovat účely, které přesahují jazyk XAML, jako jsou například podpůrné převody za běhu. Nicméně pro použití v jazyce XAML je důležité pouze cestu kódu, která může <xref:System.String> zpracovat vstup.  
  
 Druhá nejdůležitější metoda je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Je-li aplikace převedena na reprezentace kódu (například pokud je uložena do souboru XAML jako soubor), je zahrnuta ve <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> větším scénáři zapisovače textu XAML, který vytvoří reprezentace kódu. V tomto případě je důležité cesta kódu pro XAML, když volající předává a `destinationType`. <xref:System.String>  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou metody podpory, které se používají, když se služba dotazuje na <xref:System.ComponentModel.TypeConverter> možnosti implementace. Tyto metody je nutné implementovat, aby `true` se vracely na případy specifické pro typ, které odpovídají metodám převodu vašeho převaděče. Pro účely XAML to obecně znamená <xref:System.String> typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděče typů pro jazyk XAML  
 Každá <xref:System.ComponentModel.TypeConverter> implementace může jednoznačně interpretovat, co je platný řetězec pro převod, a může také použít nebo ignorovat popis typu, který je předán jako parametry. Důležitým aspektem konverze typu kultura a XAML je následující: i když použití lokalizovatelných řetězců jako hodnot atributů je v jazyce XAML podporováno, nelze použít tyto lokalizovatelné řetězce jako vstup konvertoru typu s konkrétními požadavky na jazykovou verzi. Toto omezení je způsobeno tím, že převaděče typů pro hodnoty atributů XAML zahrnují chování zpracování XAML ve fixním `en-US` jazyce, které používá jazykovou verzi. Další informace o důvodech návrhu pro toto omezení naleznete v tématu Specifikace jazyka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)) nebo [globalizace a lokalizace WPF](../wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
 Jako příklad, kdy může být jazyková verze příčinou problému, některé jazykové verze používají čárku namísto tečky jako oddělovač desetinných míst pro čísla ve formě řetězce. Toto použití koliduje s chováním, které má mnoho existujících převaděčů typů, což je použití čárky jako oddělovače. Předání jazykové verze `xml:lang` do okolního jazyka XAML problém nevyřeší.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Aby bylo možné použít jako <xref:System.ComponentModel.TypeConverter> implementaci podporující XAML <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , metoda pro tento konvertor musí jako `value` parametr přijmout řetězec. Pokud je řetězec v platném formátu a lze jej převést <xref:System.ComponentModel.TypeConverter> implementací, vrácený objekt musí podporovat přetypování na typ, který je očekáván vlastností. V opačném případě musí `null` implementacevracet.<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Každá <xref:System.ComponentModel.TypeConverter> implementace může jednoznačně interpretovat, co představuje platný řetězec pro převod, a může také použít nebo ignorovat popis typu nebo kontexty jazykové verze, které jsou předány jako parametry. Zpracování XAML jazyka WPF však nemusí předat hodnoty do kontextu popisu typu ve všech případech a také nemusí předávat jazykovou verzi založenou na `xml:lang`.  
  
> [!NOTE]
> Nepoužívejte složené závorky ({}), konkrétně levou složenou závorku ({), jako prvek formátu řetězce. Tyto znaky jsou vyhrazené jako vstupní a výstupní sekvence pro rozšíření kódu.  
  
 Je vhodné vyvolat výjimku, pokud váš konvertor typu musí mít přístup ke službě XAML z .NET Framework zapisovače objektu XAML Services, ale <xref:System.IServiceProvider.GetService%2A> volání, které je provedeno proti kontextu, nevrátí tuto službu.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>se potenciálně používá pro podporu serializace. Podpora serializace <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> prostřednictvím pro váš vlastní typ a konvertor typu není absolutní požadavek. Nicméně pokud implementujete ovládací prvek nebo použijete serializaci jako součást funkcí nebo návrh vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby bylo možné použít jako <xref:System.ComponentModel.TypeConverter> implementaci podporující jazyk XAML <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> , metoda pro tento konvertor musí přijmout instanci typu (nebo hodnotu) `value` , která je podporována jako parametr. Pokud je <xref:System.String>parametrtypu, vrácený objekt musí být schopný přetypovat jako <xref:System.String>. `destinationType` Vrácený řetězec musí představovat serializovanou hodnotu `value`. V ideálním případě by měl mít formát serializace možnost generovat stejnou hodnotu, jako kdyby byl tento řetězec předán <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementaci stejného převaděče bez významné ztráty informací.  
  
 Pokud hodnotu nelze serializovat nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementace musí vracet `null` a může vyvolat výjimku. Nicméně, pokud vyvoláte výjimky, měli byste ohlásit neschopnost použít tento převod jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace, aby bylo možné zajistit, aby byly výjimky osvědčeny <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> , aby se předešlo výjimkám.  
  
 Pokud parametr není typu <xref:System.String>, můžete zvolit vlastní zpracování převaděče. `destinationType` Obvykle se vrátíte zpět k základnímu zpracování implementace, které v <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> základu vyvolává určitou výjimku.  
  
 Je vhodné vyvolat výjimku, pokud váš konvertor typu musí mít přístup ke službě XAML z .NET Framework zapisovače objektu XAML Services, ale <xref:System.IServiceProvider.GetService%2A> volání, které je provedeno proti kontextu, nevrátí tuto službu.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementace by se `true` měla `sourceType` vrátit pro <xref:System.String> typ a jinak, odložit základní implementaci. Negenerovat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace by měla `true` vracet `destinationType` pro typ <xref:System.String>a jinak podložit základní implementaci. Negenerovat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Pro vlastní převaděč typu, který se má použít jako převaděč typu pro vlastní třídu .NET Framework XAML Services, je nutné použít <xref:System.ComponentModel.TypeConverterAttribute> na definici vaší třídy. Typ <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> , který zadáte prostřednictvím atributu, musí být název typu vašeho převaděče vlastního typu. Použijete-li tento atribut, pokud procesor XAML zpracuje hodnoty, kde typ vlastnosti používá vlastní typ třídy, může vstupní řetězce a vracet instance objektů.  
  
 Můžete také zadat konvertor typu na základě jednotlivých vlastností. Namísto použití <xref:System.ComponentModel.TypeConverterAttribute> s definicí třídy ji aplikujte na definici vlastnosti (hlavní definice, nikoli na `get` / `set` implementaci v rámci IT). Typ vlastnosti se musí shodovat s typem, který je zpracován vaším vlastním převaděčem typu. Při použití tohoto atributu, pokud procesor XAML zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vracet instance objektů. Technika konvertoru typu pro jednotlivé vlastnosti je obzvláště užitečná, pokud se rozhodnete použít typ vlastnosti z Microsoft .NET Framework nebo z jiné knihovny, kde nemůžete určit definici třídy a nemůžete <xref:System.ComponentModel.TypeConverterAttribute> použít.  
  
 Chcete-li zadat chování převodu typu pro vlastního připojeného člena, <xref:System.ComponentModel.TypeConverterAttribute> použijte `Get` pro přístupovou metodu vzoru implementace pro připojeného člena.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontextu poskytovatele služby z implementace rozšíření značek  
 Dostupné služby jsou pro libovolný převaděč hodnot stejné. Rozdíl je v tom, jak každý konvertor hodnot přijímá kontext služby. Přístup ke službám a službám, které jsou k dispozici, jsou popsány v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="type_converters_in_the_xaml_node_stream"></a>   
## <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlu XAML  
 Pokud pracujete s datovým proudem uzlu XAML, není dosud provedena akce nebo konečný výsledek převaděče typu. V cestě zatížení je řetězec atributu, který je nakonec nutné převést na typ, aby se načetl jako textová hodnota v rámci počátečního a koncového člena. Konvertor typu, který je nakonec potřebný pro tuto operaci, lze určit pomocí <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> vlastnosti. Nicméně získání platné hodnoty z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> spoléhá na, že má kontext schématu XAML, který může přistupovat k takovým informacím prostřednictvím podkladového člena, nebo typu hodnoty objektu, kterou člen používá. Vyvolání chování převodu typu také vyžaduje kontext schématu XAML, protože to vyžaduje mapování typů a vytvoření instance převaděče.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Přehled XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
