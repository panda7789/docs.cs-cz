---
title: TypeConverters a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187298"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters a XAML
Toto téma představuje účel převodu typu z řetězce jako obecné funkce jazyka XAML. V rozhraní .NET <xref:System.ComponentModel.TypeConverter> Framework slouží třída konkrétnímu účelu jako součást implementace spravované vlastní třídy, kterou lze použít jako hodnotu vlastnosti v použití atributu XAML. Pokud napíšete vlastní třídu a chcete, aby instance vaší třídy byly použitelné jako hodnoty atributů nastavitelné XAML, možná budete muset použít a <xref:System.ComponentModel.TypeConverterAttribute> pro vaši třídu, napsat vlastní <xref:System.ComponentModel.TypeConverter> třídu nebo obojí.  

## <a name="type-conversion-concepts"></a>Koncepty převodu typů  
  
### <a name="xaml-and-string-values"></a>Hodnoty XAML a řetězce  
 Když nastavíte hodnotu atributu v souboru XAML, počáteční typ této hodnoty je řetězec v čistém textu. Dokonce i další <xref:System.Double> primitiva, jako jsou zpočátku textové řetězce procesoru XAML.  
  
 Procesor XAML potřebuje ke zpracování hodnoty atributu dva kusy informací. První informace je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který je zpracován v XAML, musí být nakonec převeden nebo vyřešen na hodnotu tohoto typu. Pokud je hodnota primitivní, který je chápán analyzátorem XAML (například číselnou hodnotou), dojde k přímému převodu řetězce. Pokud je hodnota výčtu, řetězec se používá ke kontrole shody názvu s pojmenovanou konstantou v tomto výčtu. Pokud hodnota není ani parser pochopil primitivní ani výčtu, pak dotyčný typ musí být schopen poskytnout instanci typu nebo hodnotu, na základě převedeného řetězce. To se provádí označením třídy převaděče typu. Převaděč typu je efektivně pomocná třída pro poskytování hodnot jiné třídy, a to jak pro scénář XAML, tak potenciálně pro volání kódu v kódu .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Použití existujícího chování převodu typu v xaml  
 V závislosti na vaší obeznámenosti s základními koncepty XAML je možné, že již používáte chování převodu typu v základní aplikaci XAML, aniž byste si to uvědomili. Například WPF definuje doslova stovky vlastností, které <xref:System.Windows.Point>berou hodnotu typu . A <xref:System.Windows.Point> je hodnota, která popisuje souřadnici ve dvourozměrném souřadnicovém prostoru a ve skutečnosti má pouze dvě důležité vlastnosti: <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A>. Když zadáte bod v XAML, zadáte jej jako řetězec s oddělovačem (obvykle <xref:System.Windows.Point.X%2A> čárkou) mezi hodnotami a <xref:System.Windows.Point.Y%2A> hodnotami, které zadáte. Například: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 Dokonce i tento <xref:System.Windows.Point> jednoduchý typ a jeho jednoduché použití v XAML zahrnují typ ový převodník. V tomto případě je <xref:System.Windows.PointConverter>třída .  
  
 Převaděč <xref:System.Windows.Point> typu pro definované na úrovni třídy zjednodušuje <xref:System.Windows.Point>použití značek všech vlastností, které se . Bez převaděče typu zde budete potřebovat následující mnohem podrobnější značky pro stejný příklad, který byl uveden dříve:  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 Zda použít typ převodní řetězec nebo podrobnější ekvivalentní syntaxe je obecně volba stylu kódování. Pracovní postup nástrojů XAML může také ovlivnit nastavení hodnot. Některé nástroje XAML mají tendenci vyzařovat nejpodrobnější formu značky, protože je snazší round-trip na návrháře zobrazení nebo vlastní serializace mechanismus.  
  
 Existující převaděče typu lze obecně zjistit na WPF a .NET Framework typy kontrolou <xref:System.ComponentModel.TypeConverterAttribute>třídy (nebo vlastnost) na přítomnost aplikované . Tento atribut pojmenuje třídu, která je podpůrným převaděčem typu pro hodnoty tohoto typu, pro účely XAML i potenciálně pro jiné účely.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření o značky  
 Rozšíření značek a převaděče typů vyplňují ortogonové role z hlediska chování procesoru XAML a scénářů, u kterých jsou použity. Přestože kontext je k dispozici pro použití rozšíření značek, typ převodu chování vlastností, kde rozšíření značky poskytuje hodnotu je obecně není kontrolována v implementacích rozšíření značky. Jinými slovy, i když rozšíření značky vrátí `ProvideValue` textový řetězec jako svůj výstup, zadejte chování převodu na tento řetězec, jak je použito na konkrétní vlastnost nebo typ hodnoty vlastnosti není vyvolána, Obecně, účelem rozšíření značky je zpracovat řetězec a vrátit objekt bez jakéhokoli převaděče typu.  
  
 Jedna běžná situace, kdy je nutné rozšíření značek, nikoli převaděč typu, je odkaz na objekt, který již existuje. V nejlepším případě převaděč bezstavového typu může generovat pouze novou instanci, která nemusí být žádoucí. Další informace o rozšířeních značek naleznete v [tématech Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Převaděče nativního typu  
 V wpf a .NET Framework implementace analyzátoru XAML existují určité typy, které mají nativní typ zpracování převodu, ale nejsou typy, které by mohly být konvenčně považovány za primitiva. Příkladem takového typu je <xref:System.DateTime>. Důvod je založen na tom, jak funguje architektura <xref:System.DateTime> rozhraní .NET Framework: typ je definován v mscorlib, nejzákladnější knihovně v rozhraní .NET. <xref:System.DateTime>není povoleno připsat atribut, který pochází z jiného sestavení, které<xref:System.ComponentModel.TypeConverterAttribute> zavádí závislost (je ze systému), takže obvyklý mechanismus zjišťování převaděče typu přiřazením nelze podporovat. Místo toho analyzátor XAML má seznam typů, které potřebují takové nativní zpracování a zpracovává je podobně jako zpracování skutečných primitiv. (V <xref:System.DateTime> případě, že se <xref:System.DateTime.Parse%2A>jedná o volání .)  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>Implementace převaděče typů  
  
### <a name="typeconverter"></a>TypeConverter  
 V <xref:System.Windows.Point> předchozím příkladu byla <xref:System.Windows.PointConverter> uvedena třída. Pro implementací .NET XAML jsou všechny převaděče typu, které se používají <xref:System.ComponentModel.TypeConverter>pro účely XAML, třídy, které jsou odvozeny ze základní třídy . Třída <xref:System.ComponentModel.TypeConverter> existovala ve verzích rozhraní .NET Framework, které předcházejí existenci xaml; jedním z jeho původních použití bylo poskytnout převod řetězců pro dialogy vlastností ve vizuálních návrhářích. Pro XAML <xref:System.ComponentModel.TypeConverter> role je rozšířena tak, aby zahrnovala základní třídu pro převody na řetězec a z řetězce, které umožňují analýzu hodnoty atributu řetězce a případně zpracování hodnoty run-time určité vlastnosti objektu zpět do řetězce pro serializaci jako atribut.  
  
 <xref:System.ComponentModel.TypeConverter>definuje čtyři členy, které jsou důležité pro převod do a z řetězců pro účely zpracování XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z nich je <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>nejdůležitější metodou . Tato metoda převede vstupní řetězec na požadovaný typ objektu. Přísně vzato, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metoda by mohla být implementována převést mnohem širší škálu typů do zamýšleného typu určení převaděče, a tak sloužit účelům, které přesahují XAML, jako je podpora převodů za běhu, ale pro účely XAML je to pouze cesta kódu, která může zpracovat <xref:System.String> vstup, na kterém záleží.  
  
 Další nejdůležitější metodou <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>je . Pokud je aplikace převedena na reprezentaci značek (například pokud je uložena <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> do XAML jako soubor), je zodpovědná za vytvoření reprezentace značek. V tomto případě cesta kódu, která je důležitá pro `destinationType` <xref:System.String> XAML je při předání a .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou podpůrné metody, které se používají, <xref:System.ComponentModel.TypeConverter> když služba dotazuje možnosti implementace. Je nutné implementovat `true` tyto metody vrátit pro případy specifické pro typ, které ekvivalentní metody převodu podporují převaděč. Pro účely XAML to <xref:System.String> obecně znamená typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděče typů pro XAML  

 Každá <xref:System.ComponentModel.TypeConverter> implementace může mít vlastní interpretaci toho, co představuje platný řetězec pro převod a můžete také použít nebo ignorovat popis typu předaný jako parametry. Je důležité hledisko s ohledem na jazykovou verzi a převod typu XAML. Použití lokalizovatelných řetězců jako hodnot atributů je zcela podporováno xaml. Ale použití tohoto lokalizovatelného řetězce jako vstupu převaděče typů se specifickými požadavky na jazykovou verzi není podporováno, protože převaděče typů pro hodnoty atributů XAML zahrnují nutně chování analýzy pevného jazyka pomocí `en-US` jazykové verze. Další informace o důvodech návrhu tohoto omezení naleznete ve specifikaci jazyka XAML ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 Jako příklad, kde může být problém jazykové verze, některé jazykové verze používají čárku jako oddělovač desetinných bodů pro čísla. To bude kolidovat s chováním, které mají mnoho převaděčů typu WPF XAML, což je použití čárky jako oddělovače (na základě historických precedentů, jako je například společný formulář X,Y nebo seznamy oddělené čárkami). Problém nevyřeší ani předání moru `Language` `xml:lang` v `sl-SI` okolním xaml (nastavení nebo jazykové verzi, příklad jazykové verze, která používá čárku pro desetinné číslo tímto způsobem).  
  
### <a name="implementing-convertfrom"></a>Implementace convertfrom  
 Chcete-li být <xref:System.ComponentModel.TypeConverter> použitelné jako implementace, která <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> podporuje XAML, metoda pro `value` tento převaděč musí přijmout řetězec jako parametr. Pokud řetězec byl v platném formátu a <xref:System.ComponentModel.TypeConverter> může být převeden implementací, pak vrácený objekt musí podporovat přetypování na typ očekávaný vlastností. V opačném <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> případě `null`musí být implementace vrácena .  
  
 Každá <xref:System.ComponentModel.TypeConverter> implementace může mít vlastní interpretaci toho, co představuje platný řetězec pro převod a můžete také použít nebo ignorovat popis typu nebo kontexty jazykové verze předané jako parametry. Zpracování WPF XAML však nemusí předat hodnoty kontextu popisu typu ve všech případech `xml:lang`a také nemusí předat jazykovou verzi založenou na .  
  
> [!NOTE]
> Nepoužívejte znaky složené závorky, zejména {, jako možný prvek formátu řetězce. Tyto znaky jsou vyhrazeny jako položka a ukončení pro posloupnost rozšíření značek.  
  
### <a name="implementing-convertto"></a>Implementace převodu  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>je potenciálně používán pro podporu serializace. Podpora serializace <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> prostřednictvím pro vlastní typ a jeho převaděč typu není absolutní požadavek. Pokud však implementujete ovládací prvek nebo používáte serializaci jako součást funkcí nebo <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>návrhu vaší třídy, měli byste implementovat .  
  
 Chcete-li být <xref:System.ComponentModel.TypeConverter> použitelné jako implementace, která <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> podporuje XAML, metoda pro tento převaděč musí `value` přijmout instanci typu (nebo hodnoty) je podporován jako parametr. Pokud `destinationType` je parametrem <xref:System.String>typ , musí být vrácený <xref:System.String>objekt schopen být přetypován jako . Vrácený řetězec musí představovat `value`serializovanou hodnotu . V ideálním případě by měl být formát serializace, který zvolíte, schopen <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> generovat stejnou hodnotu, pokud byl tento řetězec předán implementaci stejného převaděče, bez významné ztráty informací.  
  
 Pokud hodnotu nelze serializovat nebo převaděč nepodporuje <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> serializaci, implementace musí vrátit `null`a je povoleno vyvolat výjimku v tomto případě. Ale pokud vyvoláte výjimky, měli byste nahlásit neschopnost použít <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> tento převod jako součást implementace <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> tak, aby byl podporován osvědčený postup kontroly s první, aby se zabránilo výjimkám.  
  
 Pokud `destinationType` parametr není <xref:System.String>typu , můžete zvolit vlastní zpracování převaděče. Obvykle byste se vrátit k základní zpracování implementace, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> která v basemost vyvolává konkrétní výjimku.  
  
### <a name="implementing-canconvertto"></a>Implementace canconvertto  
 Implementace <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by `true` se `destinationType` měla <xref:System.String>vrátit pro typ a jinak odložit na základní implementaci.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Implementace <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by `true` se `sourceType` měla <xref:System.String>vrátit pro typ a jinak odložit na základní implementaci.  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>Použití atributu TypeConverterAttribute  
 Aby byl převaděč vlastního typu použit jako převaděč působícího typu pro vlastní třídu procesorem XAML, musíte použít <xref:System.ComponentModel.TypeConverterAttribute> definici třídy. Zadaný <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> prostřednictvím atributu musí být název typu vlastního převaděče typu. S tímto atributem použít, když procesor XAML zpracovává hodnoty, kde typ vlastnosti používá váš vlastní typ třídy, může zadávat řetězce a vrátit instance objektu.  
  
 Můžete také zadat převaděč typu na základě vlastnosti. <xref:System.ComponentModel.TypeConverterAttribute> Místo použití definice třídy ji použijte na definici vlastnosti (hlavní definice, `get` / `set` nikoli implementace v ní). Typ vlastnosti musí odpovídat typu, který je zpracován převaděčem vlastního typu. S tímto atributem použít, když procesor XAML zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vrátit instance objektu. Technika převaděče typu vlastností je užitečná zejména v případě, že se rozhodnete použít typ vlastnosti z rozhraní <xref:System.ComponentModel.TypeConverterAttribute> Microsoft .NET Framework nebo z jiné knihovny, kde nelze řídit definici třídy a nelze použít tam.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.TypeConverter>
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
