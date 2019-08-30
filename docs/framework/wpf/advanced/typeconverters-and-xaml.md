---
title: TypeConverters a XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 8c39fe75eea5042657cab533a0a557d966802a1b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169024"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters a XAML
Toto téma zavádí účel konverze typu z řetězce jako obecné funkce jazyka XAML. V .NET Framework <xref:System.ComponentModel.TypeConverter> třída zachovává konkrétní účel jako součást implementace spravované vlastní třídy, kterou lze použít jako hodnotu vlastnosti v použití atributu XAML. Pokud píšete vlastní třídu a chcete, aby byly instance vaší třídy použitelné jako hodnoty nastavitelných atributů XAML, může být nutné použít <xref:System.ComponentModel.TypeConverterAttribute> pro třídu, zapsat vlastní <xref:System.ComponentModel.TypeConverter> třídu nebo obojí.  

## <a name="type-conversion-concepts"></a>Koncepce převodu typů  
  
### <a name="xaml-and-string-values"></a>Hodnoty XAML a řetězce  
 Když nastavíte hodnotu atributu v souboru XAML, počáteční typ této hodnoty je řetězec v čistě textu. Dokonce i jiné primitivní prvky, <xref:System.Double> jako jsou počáteční textové řetězce pro procesor XAML.  
  
 Procesor XAML potřebuje dvě části informací, aby bylo možné zpracovat hodnotu atributu. První část informací je typ hodnoty vlastnosti, kterou chcete nastavit. Libovolný řetězec, který definuje hodnotu atributu a který je zpracován v jazyce XAML, musí být nakonec převeden nebo přeložen na hodnotu tohoto typu. Pokud je hodnota primitivní, kterou považuje analyzátor XAML (jako je číselná hodnota), je proveden přímý převod řetězce. Je-li hodnotou výčet, je použit řetězec pro kontrolu shody názvu s pojmenovanou konstantou v tomto výčtu. Pokud hodnota není primitivní ani výčet srozumitelný pro analyzátor, pak musí být příslušný typ schopný poskytnout instanci typu nebo hodnotu na základě převedeného řetězce. To se provádí tak, že značí třídu konvertoru typu. Konvertor typu je efektivně pomocná třída pro poskytování hodnot jiné třídy, pro scénář XAML a také potenciálně pro volání kódu v kódu .NET.  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>Použití existujícího chování převodu typu v jazyce XAML  
 V závislosti na vaší znalosti se základními koncepty XAML můžete již v jazyce XAML pro základní aplikace použít chování převodu typů, aniž by bylo potřeba ho realizovat. Například WPF definuje doslova stovky vlastností, které přebírají hodnotu typu <xref:System.Windows.Point>. A <xref:System.Windows.Point> je hodnota, která popisuje souřadnici v dvojrozměrném prostoru souřadnic a ve skutečnosti má pouze dvě důležité vlastnosti: <xref:System.Windows.Point.X%2A> a <xref:System.Windows.Point.Y%2A>. Pokud určíte bod v jazyce XAML, zadáte ho jako řetězec s oddělovačem (obvykle čárka) mezi <xref:System.Windows.Point.X%2A> hodnotami a <xref:System.Windows.Point.Y%2A> , které zadáte. Například: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`.  
  
 I tento jednoduchý typ <xref:System.Windows.Point> a jeho jednoduché použití v jazyce XAML zahrnuje konvertor typu. V tomto případě je to třída <xref:System.Windows.PointConverter>.  
  
 Konvertor <xref:System.Windows.Point> typu, který je definován na úrovni třídy, zjednodušuje použití značek u všech vlastností, které přijmou <xref:System.Windows.Point>. Bez převaděče typu tady budete potřebovat následující mnohem přesnější značky pro stejný příklad, jak je uvedeno výše:  

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
  
 Bez ohledu na to, zda použít převodový řetězec typu nebo podrobnou syntaxi, je všeobecně Volba stylu kódování. Váš pracovní postup nástroje jazyka XAML může mít vliv také na to, jak jsou hodnoty nastaveny. Některé nástroje XAML obvykle generují nejpřesnější formu značky, protože je snazší se zpátečním zobrazením návrháře nebo jeho vlastním mechanizmem serializace.  
  
 Existující převaděče typů mohou být obecně zjišťovány u typů WPF a .NET Framework kontrolou třídy (nebo vlastnosti) pro přítomnost použité <xref:System.ComponentModel.TypeConverterAttribute>. Tento atribut pojmenuje třídu, která je podpůrného konvertoru typu pro hodnoty daného typu, pro účely XAML a také potenciálně jiné účely.  
  
### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření značek  
 Rozšíření značek a převaděče typů plní kolmé role v souvislosti s chováním procesoru XAML a scénáři, na které jsou aplikovány. Přestože je kontext k dispozici pro použití rozšíření značek, chování konverze typu vlastností, kde rozšíření značek poskytuje hodnotu obecně není zaškrtnuto v implementacích rozšíření značek. Jinými slovy, i když rozšíření značek vrátí textový řetězec jako svůj `ProvideValue` výstup, chování konverze typu u tohoto řetězce, jak je použito na konkrétní vlastnost nebo typ hodnoty vlastnosti není vyvoláno, obecně, účelem rozšíření označení je zpracování řetězec a vrátí objekt, aniž by to zahrnovalo žádný konvertor typu.  
  
 Jednou z běžných situací, kdy je rozšíření značek nezbytné místo konvertoru typu, je vytvořit odkaz na objekt, který již existuje. V optimálním případě konvertor bezstavového typu by mohl vygenerovat pouze novou instanci, která nemusí být žádoucí. Další informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
### <a name="native-type-converters"></a>Převaděče nativního typu  
 V WPF a .NET Framework implementaci analyzátoru XAML existují určité typy, které mají zpracování převodu nativního typu, ale nejsou typy, které by mohly být považovány za primitivní. Příklad takového typu je <xref:System.DateTime>. Důvod je založený na tom, jak architektura .NET Framework funguje: typ <xref:System.DateTime> je definován v knihovně Mscorlib, nejvíce základní knihovna rozhraní .NET. <xref:System.DateTime>není povoleno mít atribut s atributem, který pochází z jiného sestavení, které zavádí závislost (<xref:System.ComponentModel.TypeConverterAttribute> je ze systému), aby běžný mechanismus zjišťování konvertoru typu, který se dodávají, nemohl být podporován. Místo toho má analyzátor XAML seznam typů, které vyžadují takové nativní zpracování a zpracovává je podobně jak jsou zpracovávány skutečné primitivy. (V případě <xref:System.DateTime> tohoto případu zahrnuje <xref:System.DateTime.Parse%2A>volání.)  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>Implementace konvertoru typu  
  
### <a name="typeconverter"></a>TypeConverter  
 V předchozím <xref:System.Windows.PointConverter> příkladu bylo zmíněno třídy. <xref:System.Windows.Point> U implementací rozhraní XAML pro .NET jsou všechny převaděče typu, které jsou používány pro účely XAML, třídy odvozené ze <xref:System.ComponentModel.TypeConverter>základní třídy. <xref:System.ComponentModel.TypeConverter> Třída existovala ve verzích .NET Framework, které předcházejí existenci XAML; jedno z jeho původních použití bylo poskytnout převod řetězce pro dialogy vlastností v vizuálních návrhářích. Pro XAML <xref:System.ComponentModel.TypeConverter> je role rozbalená tak, aby zahrnovala základní třídu pro řetězcové převody a převody z řetězce, které umožňují analýzu hodnoty řetězcového atributu, a případně zpracování běhové hodnoty pro konkrétní vlastnost objektu zpět do řetězce pro serializace jako atribut.  
  
 <xref:System.ComponentModel.TypeConverter>definuje čtyři členy, které jsou relevantní pro převod na a z řetězců pro účely zpracování XAML:  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Nejdůležitější metodou je <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>. Tato metoda převede vstupní řetězec na požadovaný typ objektu. Výhradně řečeno, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> metodu lze implementovat pro převod mnohem širšího rozsahu typů do zamýšleného cílového typu převaděče, a proto slouží pro účely rozšíření kódu XAML, jako jsou podpůrné převody za běhu, ale pro účely XAML. je to pouze cesta kódu, která může zpracovat vstup <xref:System.String> , který záleží na tom.  
  
 Další nejdůležitější metodou je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud je aplikace převedena na reprezentace kódu (například pokud je uložena do souboru XAML jako soubor), <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> zodpovídá za vytvoření reprezentace kódu. V tomto případě je v případě, že je předáte `destinationType` z <xref:System.String> , cesta kódu, která je v jazyce XAML.  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou metody podpory, které se používají, když se služba dotazuje na <xref:System.ComponentModel.TypeConverter> možnosti implementace. Tyto metody je nutné implementovat, aby `true` se vracely na případy specifické pro typ, které odpovídají metodám převodu vašeho převaděče. Pro účely XAML to obecně znamená <xref:System.String> typ.  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděče typů pro jazyk XAML  
 Každá <xref:System.ComponentModel.TypeConverter> implementace může mít vlastní výklad toho, co představuje platný řetězec pro převod, a může také použít nebo ignorovat popis typu předaný jako parametry. Je důležité zvážit v souvislosti s převodem typu kultury a XAML. Použití lokalizovatelných řetězců jako hodnot atributů je v jazyce XAML zcela podporováno. Ale použití tohoto lokalizovatelnýho řetězce jako vstupu konvertoru typu s konkrétními jazykovými požadavky není podporováno, protože převaděče typů pro hodnoty atributů XAML zahrnují chování při analýze pevného jazyka, `en-US` které používá jazykovou verzi. Další informace o návrhových důvodech pro toto omezení byste měli prostudovat ve specifikaci jazyka XAML ([\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)).  
  
 Jako příklad, kde může být jazyková verze příčinou problému, některé jazykové verze používají čárku jako oddělovač desetinných míst pro čísla. Dojde k kolizi s chováním, které mají mnoho převaděčů typu XAML jazyka WPF, což znamená použití čárky jako oddělovače (na základě historických předchůdců, jako jsou například Common X, Y nebo seznam oddělených čárkami). Ani předání jazykové verze ve okolním jazyce XAML ( `Language` nastavení `xml:lang` nebo na `sl-SI` jazykovou verzi, jako příklad jazykové verze, která používá čárku pro desetinné místo) neřeší problém.  
  
### <a name="implementing-convertfrom"></a>Implementace ConvertFrom  
 Aby bylo možné použít jako <xref:System.ComponentModel.TypeConverter> implementaci podporující XAML <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> , metoda pro tento konvertor musí jako `value` parametr přijmout řetězec. Pokud má řetězec v platném formátu a lze jej převést pomocí <xref:System.ComponentModel.TypeConverter> implementace, vrácený objekt musí podporovat přetypování na typ očekávaný vlastností. V opačném případě musí `null` implementacevracet.<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 Každá <xref:System.ComponentModel.TypeConverter> implementace může mít vlastní výklad toho, co představuje platný řetězec pro převod, a může také použít nebo ignorovat popis typu nebo kontexty jazykové verze předané jako parametry. Zpracování XAML jazyka WPF však nemusí předat hodnoty do kontextu popisu typu ve všech případech a také nemusí předávat jazykové verze založené na `xml:lang`.  
  
> [!NOTE]
> Nepoužívejte znaky složených závorek, zejména {, jako možný prvek formátu řetězce. Tyto znaky jsou vyhrazené jako vstupní a výstupní sekvence pro rozšíření kódu.  
  
### <a name="implementing-convertto"></a>Implementace ConvertTo  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>se potenciálně používá pro podporu serializace. Podpora serializace <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> prostřednictvím pro váš vlastní typ a konvertor typu není absolutní požadavek. Nicméně pokud implementujete ovládací prvek nebo použijete serializaci jako součást funkcí nebo návrh vaší třídy, měli byste implementovat <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>.  
  
 Aby bylo možné použít jako <xref:System.ComponentModel.TypeConverter> implementaci podporující XAML <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> , metoda pro tento konvertor musí přijmout instanci typu (nebo hodnotu `value` ) podporovanou jako parametr. Pokud je <xref:System.String>parametrtypu, vrácený objekt musí být schopný přetypovat jako <xref:System.String>. `destinationType` Vrácený řetězec musí představovat serializovanou hodnotu `value`. V ideálním případě by měl být zvolený formát serializace schopný generovat stejnou hodnotu, pokud byl tento řetězec předán <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> implementaci stejného převaděče bez významné ztráty informací.  
  
 Pokud hodnota nemůže být serializována nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementace musí vracet `null`a je povoleno vyvolat výjimku v tomto případě. Ale pokud vyvoláte výjimky, měli byste ohlásit neschopnost použít tento převod jako součást vaší <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace tak, aby byl doporučený postup kontroly s <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> prvními, aby se výjimky vyhnuly.  
  
 Pokud `destinationType` parametr není typu <xref:System.String>, můžete zvolit vlastní zpracování převaděče. Obvykle byste měli obnovit základní zpracování implementace, které v basemost <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> vyvolává konkrétní výjimku.  
  
### <a name="implementing-canconvertto"></a>Implementace CanConvertTo  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> implementace by měla `true` vracet `destinationType` pro typ <xref:System.String>a jinak podložit základní implementaci.  
  
### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom  
 Vaše <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> implementace by měla `true` vracet `sourceType` pro typ <xref:System.String>a jinak podložit základní implementaci.  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>Použití TypeConverterAttribute  
 Aby byl váš vlastní konvertor typu použit jako převaděč jako typ pro vlastní třídu procesorem XAML, je nutné použít <xref:System.ComponentModel.TypeConverterAttribute> pro definici vaší třídy. Typ <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> , který zadáte prostřednictvím atributu, musí být název typu vašeho převaděče vlastního typu. Při použití tohoto atributu, když procesor XAML zpracovává hodnoty, kde typ vlastnosti používá vlastní typ třídy, může vstupní řetězce a vracet instance objektů.  
  
 Můžete také zadat konvertor typu na základě jednotlivých vlastností. Namísto použití <xref:System.ComponentModel.TypeConverterAttribute> s definicí třídy ji aplikujte na definici vlastnosti (hlavní definice, nikoli na `get` / `set` implementaci v rámci IT). Typ vlastnosti se musí shodovat s typem, který je zpracován vaším vlastním převaděčem typu. Při použití tohoto atributu, pokud procesor XAML zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vracet instance objektů. Technika konvertoru typu pro jednotlivé vlastnosti je obzvláště užitečná, pokud se rozhodnete použít typ vlastnosti z Microsoft .NET Framework nebo z jiné knihovny, kde nemůžete určit definici třídy a nemůžete <xref:System.ComponentModel.TypeConverterAttribute> použít.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.TypeConverter>
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
- [Podrobná syntaxe XAML](xaml-syntax-in-detail.md)
