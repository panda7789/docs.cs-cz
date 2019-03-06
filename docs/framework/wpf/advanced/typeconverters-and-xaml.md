---
title: TypeConverters a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 7f42bb6e4333fcb5e83ee4b95e404230424b317f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352708"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters a XAML
Toto téma popisuje účel typu Převod z řetězce jako obecnou funkcí jazyka XAML. V rozhraní .NET Framework <xref:System.ComponentModel.TypeConverter> třída slouží jako součást implementace pro spravovaný vlastní třídu, která lze použít jako hodnotu vlastnosti v použití atributu XAML konkrétní účel. Pokud napíšete vlastní třída a chcete, aby instance třídy má být použitelná jako hodnoty atributů nastavitelné XAML, může být potřeba použít <xref:System.ComponentModel.TypeConverterAttribute> do vaší třídy napsat vlastní <xref:System.ComponentModel.TypeConverter> třídy, nebo obojí.  
  

  
## <a name="type-conversion-concepts"></a>Typ převodu koncepty  
  
### <a name="xaml-and-string-values"></a>XAML a hodnotami řetězců  
 Když nastavíte hodnotu atributu v souboru XAML, počáteční typ tato hodnota je řetězec v čistě textovým. Dokonce i v dalších primitivních elementů, jako <xref:System.Double> jsou zpočátku textových řetězců, které procesor XAML.  
  
 Procesor XAML vyžaduje dva druhy údajů aby bylo možné zpracovat hodnotu atributu. První část informací je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který, jsou zpracovávána v XAML musí být nakonec převést nebo přeložit hodnotu daného typu. Pokud je hodnota jednoduchého typu, který je srozumitelné pro analyzátor XAML (například číselná hodnota), dojde k pokusu o přímý převod řetězce. Pokud je hodnota výčtu, řetězec se používá ke kontrole pro porovnání název pojmenované konstanty tohoto výčtu. Pokud je hodnota ani na primitivní analyzátor rozumí ani výčet a dotyčný typ musí být schopný poskytnout instanci typu, nebo hodnotu založenou na převedený řetězec. To se provádí tak, že třída konvertor typu. Konvertor typů je v podstatě pomocnou třídu pro poskytování hodnoty jiné třídy, pro scénář XAML a potenciálně také pro kód volá v kódu .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Pomocí stávající chování převodu typu v XAML  
 V závislosti na vaší znalost základní koncepty XAML už využíváte chování převodu typu v základní aplikaci XAML nevěděli ho. Například WPF definuje doslova stovky vlastnosti, které přijmout hodnotu typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> je hodnota, která popisuje souřadnice v dvojrozměrné souřadnicového prostoru a vlastně jenom má dvě důležité vlastnosti: <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A>. Při zadávání bod v XAML můžete zadat jako řetězec s oddělovačem (obvykle čárkami) mezi <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A> hodnoty, které zadáte. Například: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 I tento jednoduchý typ <xref:System.Windows.Point> a využití jednoduché v XAML zahrnují konvertor typu. V tomto případě to je třída <xref:System.Windows.PointConverter>.  
  
 Konvertor typů pro <xref:System.Windows.Point> definované na úrovni zjednodušují třídy použití značek všech vlastností, které trvat <xref:System.Windows.Point>. Bez konvertor typu tady, je třeba následující mnohem podrobnější kód pro stejný příklad uvedený dříve:  

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
  
 Jestli se má použít typ převodu řetězce nebo podrobnější ekvivalentní syntax je obecně kódování styl volbou. Pracovního postupu nástroje XAML může také ovlivnit, jak nastavit hodnoty. Některé nástroje XAML se mají generovat nejpodrobnější formu značky vzhledem k tomu je snazší zpátečního převodu na návrháře zobrazení nebo svůj vlastní mechanismus serializace.  
  
 Obecně je možné zjistit existující typ převaděče na typy WPF a .NET Framework pomocí třídy (nebo vlastnost) zjišťuje přítomnost použité <xref:System.ComponentModel.TypeConverterAttribute>. Tento atribut se název třídy, která je podpůrné konvertor typu pro hodnoty tohoto typu, pro účely XAML také potenciálně jiným účelům.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Rozšíření a typ převaděče značek vyplnit ortogonální role z hlediska procesoru chování XAML a scénáře, které se použijí pro. I když je k dispozici pro použití rozšíření značky kontext, není chování převodu typu vlastnosti, kde rozšíření značek zajišťuje, že hodnota je obecně změnami implementace rozšíření značek. Jinými slovy i v případě, že rozšíření značek vrací textový řetězec jako jeho `ProvideValue` výstupu, není vyvolána chování převodu typu pro tento řetězec jako použitý pro určitou vlastnost nebo typ hodnoty vlastnosti, obecně je účel rozšíření značek k procesu řetězce a vrátit potřebný objekt bez jakékoli konvertor typu.  
  
 Jedna běžné situace, kde je nutné místo konvertor typu rozšíření značek, je vytvořit odkaz na objekt, který již existuje. Konvertor typu bezstavové nejlépe, může generovat jenom nové instance, který nemusí být žádoucí. Další informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Nativní typ převaděče  
 V implementaci WPF a .NET Framework XAML analyzátor existují určité typy, které mají nativní typ převodu zpracování, ještě nejsou typy, které může konvenčně považovat za primitiv. Příklad takového typu je <xref:System.DateTime>. Důvodem je založen na fungování architektury .NET Framework: typ <xref:System.DateTime> je definována v mscorlib, většina základních knihoven v .NET. <xref:System.DateTime> není dovoleno přiřadit atributem, který pochází z jiného sestavení, který vytvoří závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému), nemůže být podporována mechanismu obvykle typ převaděče zjišťování přidělování. Místo toho analyzátoru XAML obsahuje seznam typů, které je třeba tyto nativní zpracování a zpracuje podobně do zpracování true primitiv. (V případě třídy <xref:System.DateTime> to zahrnuje volání <xref:System.DateTime.Parse%2A>.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace konvertor typu  
  
### <a name="typeconverter"></a>TypeConverter  
 V <xref:System.Windows.Point> příklad dříve uvedeného třídy <xref:System.Windows.PointConverter> zmíněné. Pro implementace .NET XAML, všechny převaděče typů, které se používají pro účely XAML jsou třídy, které jsou odvozeny od základní třídy <xref:System.ComponentModel.TypeConverter>. <xref:System.ComponentModel.TypeConverter> Třídy existuje ve verzích rozhraní .NET Framework, které předcházet existenci XAML; jedno z jeho původní použití bylo převodu řetězce pro dialogová okna vlastnosti ve vizuální návrhářské nástroje. Pro XAML, role <xref:System.ComponentModel.TypeConverter> rozbalen a zahrnují se základní třída pro převody na řetězec a z řetězce, které umožňují analýzu řetězcovou hodnotu atributu a pravděpodobně zpracování za běhu hodnotu vlastnosti konkrétního objektu zpět do řetězce pro serializace jako atribut.  
  
 <xref:System.ComponentModel.TypeConverter> definuje čtyři členy, které jsou relevantní pro převod do a z řetězce pro účely zpracování XAML:  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Z nich je nejdůležitější způsob <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Tato metoda převede vstupní řetězec na typ požadovaný objekt. Přesněji řečeno <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> mnohem širší škálu typy převést na typ převaděče požadovaného cíle, a proto mají účely, které přesahují XAML, jako je například podpory převodů za běhu, ale pro účely XAML může implementovat – metoda je jenom do cesty kódu, která dokáže zpracovávat <xref:System.String> vstup, který je důležité.  
  
 Další nejdůležitější způsob je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud aplikace je převedena na reprezentaci značky (například pokud je uložen jako soubor XAML), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> je zodpovědný za vytváření reprezentaci značky. V takovém případě je do cesty kódu, který je důležité pro XAML při předání `destinationType` z <xref:System.String> .  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou metody podpory, které se používají, když služba dotazuje možnosti <xref:System.ComponentModel.TypeConverter> implementace. Je nutné implementovat tyto metody k vrácení `true` pro konkrétní typ, který odpovídá převod metody vaše konvertoru podporují. Pro účely XAML to obvykle znamená, <xref:System.String> typu.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděčů typů pro XAML  
 Každý <xref:System.ComponentModel.TypeConverter> implementace může mít svůj vlastní interpretaci co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat popis typu předány jako parametry. Je důležitým aspektem, který jde o jazykové verzi a převod typu XAML. Použití zdrojů lokalizovatelných řetězců jako hodnoty atributů zcela podporuje XAML. Ale pomocí tohoto zdrojů lokalizovatelných řetězců jako vstupní typ převaděče s požadavky na konkrétní jazykové verze se nepodporuje, protože převaděčů typů pro hodnoty atributů XAML zahrnují analýzy chování nutně oprava jazyka, pomocí `en-US` jazykovou verzi. Další informace o návrhu důvody pro toto omezení, měli byste se obrátit specifikace jazyka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Jako příklad, kde jazykovou verzi může být problém některé jazykové verze používají čárku jako oddělovač jejich desetinné čárky pro čísla. To bude kolidují s chování, které mají mnoho převaděče typů WPF XAML, který se má použít čárku jako oddělovač (podle historických předchůdci, jako je například běžné X, Y formuláře nebo čárkami oddělený seznam). Jazykovou verzi i předávajícího okolního XAML (nastavení `Language` nebo `xml:lang` k `sl-SI` jazykovou verzi, příklad jazykovou verzi, která používá jako desítkové číslo v tímto způsobem) se problém nevyřeší.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Má být použitelná jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metoda pro tento převodník musí přijímat jako řetězec `value` parametr. Pokud řetězec byl platný formát a můžete převést pomocí <xref:System.ComponentModel.TypeConverter> implementace pak vráceného objektu musí podporovat přetypování na typ očekávaný vlastností. V opačném případě <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> musí vracet implementace `null`.  
  
 Každý <xref:System.ComponentModel.TypeConverter> implementace může mít svůj vlastní interpretaci co se považuje za platný řetězec pro převod a můžete také použít nebo ignorovat typ popis nebo jazykovou verzi kontexty předány jako parametry. Však nemusí předat hodnoty do kontextu popis typu ve všech případech WPF XAML zpracování a také nemusí předat na základě jazykové verze `xml:lang`.  
  
> [!NOTE]
>  Nepoužívejte znaky složených závorek, zejména {, jako je to možné element řetězec formátu. Tyto znaky jsou rezervované jako vstupní a výstupní pořadí rozšíření značek.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> potenciálně se používá pro podporu serializace. Podpora serializace prostřednictvím <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> pro vlastní typ a jeho typ převaděče není jasný požadavek. Nicméně, pokud jsou implementaci ovládacího prvku, nebo pomocí serializace jako součást funkcí nebo návrhu vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Má být použitelná jako <xref:System.ComponentModel.TypeConverter> implementace, která podporuje XAML, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> metody pro tento převodník musí přijmout instance typu (nebo hodnotu) se nepodporuje, jako `value` parametr. Když `destinationType` parametr je typ <xref:System.String>, vrácený objekt musí být schopné provést přetypování jako <xref:System.String>. Vrácený řetězec musí představovat serializovaná hodnota `value`. V ideálním případě by měly být schopné generování stejnou hodnotu, pokud bylo předáno tento řetězec formát serializace zvolíte <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementace konvertoru stejné bez výrazné ztráty informací.  
  
 Pokud hodnotu nelze serializovat nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> musí vracet implementace `null`a je povolen v tomto případě vyvolání výjimky. Ale pokud vyvolat výjimky, ohlaste nemožnosti převodu používat jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace tak, aby osvědčený postup kontroly s <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> nejprve výjimky, aby se podporuje.  
  
 Pokud `destinationType` parametr není typu <xref:System.String>, můžete použít vlastní převodník zpracování. Obvykle by vrátit do základní implementace zpracování, což je v basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolá určité výjimky.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by měla vrátit implementaci `true` pro `destinationType` typu <xref:System.String>a v opačném případě odložit na základní implementaci.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by měla vrátit implementaci `true` pro `sourceType` typu <xref:System.String>a v opačném případě odložit na základní implementaci.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Aby vaše vlastní konvertor typu pro použití jako jednající konvertor typu pro třídu vlastního procesoru XAML, je nutné použít [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definice třídy. <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> Určenou prostřednictvím atributu musí být název typu konvertoru vlastního typu. Pomocí tohoto atributu se použije když procesor XAML zpracovává hodnoty, kde typ vlastnosti používá typ vaše vlastní třídy, může vstupních řetězců a vrátí instance objektů.  
  
 Můžete také zadat konvertor typu na jednotlivých vlastností. Místo použití [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> do definice třídy, použijte ji pro definici vlastnosti (hlavní definice není `get` / `set` implementace v rámci něj). Typ vlastnosti musí odpovídat typ, který zpracovává vaše vlastní konvertor typu. Pomocí tohoto atributu se použije když XAMLprocessor zpracovává hodnoty této vlastnosti, se můžou zpracovávat vstupního řetězce a vrátí instance objektů. Na vlastnost typ převaděče technika je zvlášť užitečné, pokud se rozhodnete použít typ vlastnosti z rozhraní Microsoft .NET Framework nebo z některé jiné knihovny, kde nemůžeme mít pod kontrolou definice třídy a nejde použít <xref:System.ComponentModel.TypeConverterAttribute> existuje.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ComponentModel.TypeConverter>
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
