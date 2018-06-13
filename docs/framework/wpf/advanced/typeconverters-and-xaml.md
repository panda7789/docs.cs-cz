---
title: TypeConverters a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: a6d41b5ad519302016ed7fa1d6a103af0f4f14d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549679"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters a XAML
Toto téma představuje účelem převodu typu z řetězce jako obecné funkce jazyka XAML. V rozhraní .NET Framework <xref:System.ComponentModel.TypeConverter> třída slouží jako součást implementace pro spravované vlastní třídu, která lze použít jako hodnoty vlastností v použití atributu XAML určitý účel. Pokud můžete psát vlastní třídu a chcete instancí vaší třídy možné používat jako hodnoty nastavit atribut XAML, může se mají použít <xref:System.ComponentModel.TypeConverterAttribute> na třídu, zápis vlastní <xref:System.ComponentModel.TypeConverter> třídy, nebo obojí.  
  

  
## <a name="type-conversion-concepts"></a>Koncepty převody typu  
  
### <a name="xaml-and-string-values"></a>XAML a hodnotami řetězců  
 Když nastavíte hodnotu atributu v souboru XAML, počáteční typ této hodnoty je řetězec v čistě textovým. I další primitiv jako <xref:System.Double> jsou původně textové řetězce pro procesor XAML.  
  
 Procesor XAML musí dva druhy údajů aby bylo možné zpracovat hodnotu atributu. První část informace je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který zpracovává v jazyce XAML musí být nakonec převést nebo byl přeložen na hodnotu daného typu. Pokud je hodnota Primitivum, které se rozumí analyzátor jazyka XAML (například číselnou hodnotu), dojde k pokusu o přímé převod řetězce. Pokud je hodnota výčtu, řetězec se používá ke kontrole shody název pojmenovaného konstantu tohoto výčtu. Pokud je hodnota ani rozumí analyzátor primitivní ani výčet a pak v typu musí být schopen poskytnout instance typu nebo hodnotu, na základě převedený řetězce. Děje se tak, že zadáte třídu typ převaděče. Převaděče typů je efektivně pomocná třída pro zajištění hodnoty jiné třídy, pro scénář XAML a potenciálně také pro volání kódu v rozhraní .NET kódu.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Pomocí chování převod existující typ v jazyce XAML  
 V závislosti na vaší znalost základní koncepty XAML již používáte typ převodu chování v základní aplikace XAML bez porozumění ho. Například WPF definuje oznámena stovky vlastnosti, které trvat hodnotu typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> je hodnota, která popisuje souřadnice v dvojrozměrném prostoru souřadnic a pouze má dvě důležité vlastnosti: <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A>. Pokud určíte bod v jazyce XAML, můžete je zadat jako řetězec s oddělovačem (obvykle čárkou) mezi <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A> hodnoty, které zadáte. Příklad: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1">`.  
  
 I tento jednoduchý typ <xref:System.Windows.Point> a jeho jednoduché využití v jazyce XAML zahrnovat převaděče typů. V takovém případě se třída <xref:System.Windows.PointConverter>.  
  
 Převaděč typů pro <xref:System.Windows.Point> definované na úrovni zjednodušuje třída použití značek všech vlastností, které provést <xref:System.Windows.Point>. Bez převaděče typu zde, je nutné následující mnohem podrobnější kód pro příkladě uvedený výše:  
  
 `<LinearGradientBrush>`  
  
 `<LinearGradientBrush.StartPoint>`  
  
 `<Point X="0" Y="0"/>`  
  
 `</LinearGradientBrush.StartPoint>`  
  
 `<LinearGradientBrush.EndPoint>`  
  
 `<Point X="1" Y="1"/>`  
  
 `</LinearGradientBrush.EndPoint>`  
  
 `<LinearGradientBrush>`  
  
 Jestli se má použít převod řetězce typu nebo podrobnější ekvivalentní syntaxe je obecně kódování volba stylu. Pracovní postup nástrojů XAML, můžou také ovlivnit jak hodnoty jsou nastavené. Některé nástroje XAML zpravidla emitování nejpodrobnější formu kód, protože je jednodušší operace round-trip pro návrháře zobrazení nebo svůj vlastní mechanismu serializace.  
  
 Existující převaděče typů můžete zjistit obecně na typy WPF a rozhraní .NET Framework – třída (nebo vlastnost) vyhledáním přítomnost použité <xref:System.ComponentModel.TypeConverterAttribute>. Tento atribut bude název třída, která je podpůrné převaděč typů pro hodnoty tohoto typu, pro účely XAML a také potenciálně jiné účely.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Rozšíření a typ převaděče značek plnění ortogonální rolí z hlediska chování procesoru XAML a scénáře, které se použijí pro. I když kontext je k dispozici pro použití rozšíření značek, chování převodu typu vlastností, kde rozšíření značek poskytuje že hodnotu je obecně kontrolována v implementacích rozšíření značek. Jinými slovy i v případě, že rozšíření značek vrátí textový řetězec jako jeho `ProvideValue` výstup, není-li vyvolána typ převodu chování na tento řetězec jako použít pro určitou vlastnost nebo typ hodnoty vlastnosti, obecně, účelem rozšíření značek je zpracovat řetězec a vrátí objekt bez jakékoli převaděče typů související se situací.  
  
 Jeden běžné situaci, kde je nutné místo převaděče typů rozšíření značek je odkaz na objekt, který již existuje. Převaděč bezstavové typu, může generovat jenom novou instanci, která nemusí být žádoucí. Další informace o rozšíření značek v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Převaděče nativním typu  
 Implementace WPF a rozhraní .NET Framework XAML analyzátor existují určité typy, které mají nativní typ převodu zpracování, ještě nejsou typy, které může být obvykle považovat za primitiv. Příkladem takového typu je <xref:System.DateTime>. Důvodem je založena na tom, jak funguje Architektura rozhraní .NET Framework: typ <xref:System.DateTime> je definována v mscorlib, nejzákladnější knihovny v rozhraní .NET. <xref:System.DateTime> nemá oprávnění k být opatřená atribut, který pochází z jiného sestavení, které představuje závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému), mechanismus obvyklé typ převaděče zjišťování pomocí zapisujících nemůže být podporováno. Místo toho analyzátor jazyka XAML má seznam typů, které je třeba tyto nativní zpracování a stejně tak, aby zpracování true primitiv zpracovává. (U <xref:System.DateTime> to zahrnuje volání <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace převaděče typů  
  
### <a name="typeconverter"></a>TypeConverter  
 V <xref:System.Windows.Point> příklad dřív zadána třída <xref:System.Windows.PointConverter> jsme mluvili. Pro implementace rozhraní .NET XAML, jsou všechny převaděče typů, které se používají pro účely XAML třídy, které jsou odvozeny od základní třídy <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Třída existovaly ve verzích rozhraní .NET Framework, které předcházet existenci XAML; byl jeden z jeho původní použití zajistit převod řetězce pro vlastnost dialogová okna v vizuální nástroje. Pro jazyk XAML, role <xref:System.ComponentModel.TypeConverter> je rozšířit, aby obsahovaly se základní třídu pro na řetězec a z řetězce převody, které umožňují analýzy řetězcovou hodnotu atributu a pravděpodobně zpět do řetězce pro zpracování hodnota doby běhu vlastnosti konkrétního objektu serializace jako atribut.  
  
 <xref:System.ComponentModel.TypeConverter> definuje čtyři členy, které jsou relevantní pro převod na a z řetězce pro zpracování XAML pro účely:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z těchto, je nejdůležitější metody <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Tato metoda převede vstupní řetězec na typ požadovaný objekt. Přesněji řečeno <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> může být implementována metoda mnohem širší rozsah typy převést na typ určený cíle tento převaděč, a proto slouží k účelům, které přesahují XAML, jako je podpora převody spuštění, ale pro účely XAML je pouze kódová cesta, která může zpracovat <xref:System.String> vstup, záleží.  
  
 Další metodou nejdůležitější je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud aplikace jsou převedeny na znázornění značek (například pokud je uložen do XAML jako soubor), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zodpovídá za vytvoření znázornění značek. V takovém případě je kód cestu, která záleží pro jazyk XAML při předání `destinationType` z <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> podporu metod, které se použijí při služby dotazuje možnosti <xref:System.ComponentModel.TypeConverter> implementace. Je nutné implementovat tyto metody vrátit `true` pro konkrétní typ případů, které podporují převod ekvivalentní metody vaší převaděč. Pro účely XAML to obvykle znamená <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi, převaděčů typů pro jazyk XAML  
 Každý <xref:System.ComponentModel.TypeConverter> implementace může mít svůj vlastní výklad co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat popis typu předány jako parametry. Je důležitý faktor s ohledem na jazykovou verzi a převod typů XAML. Pomocí možnosti lokalizace řetězce jako hodnoty atributů zcela podporuje XAML. Ale pomocí tohoto lokalizovatelný řetězce jako vstupní typ převaděče s požadavky na konkrétní jazykové verze není podporována, převaděčů typů pro hodnoty atributu XAML totiž analýzy chování nutně pevné jazyk, pomocí `en-US` jazykovou verzi. Další informace o návrhu důvody pro toto omezení by se měli obrátit specifikace jazyka XAML ([\[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Jako příklad, kdy jazykovou verzi může být problém některé jazykové verze použít čárku jako jejich oddělovač desetinných čísel. To bude v konfliktu s chování, které máte spoustu převaděče typů WPF XAML, který má používat jako oddělovač čárkou (založená na historické vstupních hodnot, jako je například běžné X, Y formuláře nebo čárkami oddělený seznamy). I předávání jazykovou verzi v okolního XAML (nastavení `Language` nebo `xml:lang` k `sl-SI` jazykovou verzi, příklad jazykovou verzi, která používá jako decimal tímto způsobem) problém nevyřeší.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Možné používat jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metodu pro tento převaděč musí přijmout řetězec jako `value` parametr. Pokud řetězec byl v platné, formátování a mohou být pomocí převedeny <xref:System.ComponentModel.TypeConverter> implementace pak vráceného objektu musí podporovat přetypování na typ očekávaný vlastností. Jinak <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musí vracet implementace `null`.  
  
 Každý <xref:System.ComponentModel.TypeConverter> implementace může mít svůj vlastní výklad co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat typ popis nebo jazykovou verzi kontexty předány jako parametry. Však nemusí předat hodnoty do kontextu popis typu ve všech případech XAML WPF zpracování a nemusí předat také jazykovou verzi na základě `xml:lang`.  
  
> [!NOTE]
>  Nepoužívejte znaky složené závorky, zejména {, jako element možné vámi řetězec formátu. Tyto znaky jsou vyhrazené jako vstup a výstup pro rozšíření pořadí značek.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potenciálně se používá pro podporu serializace. Podpora serializace prostřednictvím <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro vlastní typ a jeho typ není převaděč absolutní požadavek. Ale pokud jsou implementaci ovládacího prvku, nebo pomocí serializace jako součást funkce nebo návrh vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Možné používat jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metodu pro tento převaděč musí přijmout instanci typu (nebo hodnotu) není podporována, jako `value` parametr. Když `destinationType` parametr je typ <xref:System.String>, pak vráceného objektu musí být schopen převést jako <xref:System.String>. Vrácený řetězec musí představovat serializovaná hodnota `value`. V ideálním případě by mělo být možno generování stejnou hodnotu, pokud bylo předáno tento řetězec formát serializace zvolíte <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementace stejné převaděč bez významné ztrátě informací.  
  
 Pokud hodnota nemůže být serializován nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musí vracet implementace `null`a je umožnit v tomto případě vyvolat výjimku. Ale pokud generování výjimek, byste měli hlásit nemožnost použít tento převod jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace tak, aby osvědčený postup, kontrola s <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> nejprve vyhnout výjimky se podporuje.  
  
 Pokud `destinationType` parametr není typu <xref:System.String>, můžete zvolit vlastní převaděč zpracování. Obvykle se vrátit k základní implementaci zpracování, které v basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolá určité výjimky.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by měla vrátit implementace `true` pro `destinationType` typu <xref:System.String>a jinak odložení základní implementaci.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by měla vrátit implementace `true` pro `sourceType` typu <xref:System.String>a jinak odložení základní implementaci.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Aby vaše vlastní typ převaděče má být použit jako funguje převaděč typů pro vlastní třídu s procesorem XAML, musíte použít [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do vaší definice třídy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Zadáte prostřednictvím atributu musí být název typu vaše vlastní typ převaděče. K tomuto atributu se použije když XAML procesor zpracovává hodnoty, kde typ vlastnosti používá typ vaše vlastní třídy, může vstup řetězce a vrátí instance objektů.  
  
 Převaděče typů můžete zadat taky na jednotlivých vlastností. Místo použití [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> v definici třídy použijte ho pro definici vlastnosti (hlavní definice není `get` / `set` implementace v něm). Typ vlastnosti musí odpovídat typ, který zpracovává vaše vlastní typ převaděče. K tomuto atributu se použije když XAMLprocessor zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vrátí instance objektů. Postup pro vlastnosti typu převaděč je zvláště užitečné, pokud chcete použít typ vlastnosti z rozhraní Microsoft .NET Framework nebo z některé jiné knihovny, kde nemůže ovládat definice třídy a nelze použít <xref:System.ComponentModel.TypeConverterAttribute> existuje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.TypeConverter>  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [Podrobná syntaxe XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
