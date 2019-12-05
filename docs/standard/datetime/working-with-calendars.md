---
title: Práce s kalendáři
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
ms.openlocfilehash: de8e5a03c769a22f3320c7785706555898bf8c1c
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802736"
---
# <a name="work-with-calendars"></a>Práce s kalendáři

Ačkoli hodnoty data a času představují konkrétní časový okamžik, je řetězcové vyjádření závislé na jazykové verzi a závisí jak na konvencích použitých k zobrazení hodnoty data a času podle konkrétní jazykové verze, tak na kalendáři používaném danou jazykovou verzí. Toto téma popisuje podporu pro kalendáře v rozhraní .NET a popisuje použití tříd kalendáře při práci s hodnotami data.

## <a name="calendars-in-net"></a>Kalendáře v .NET

Všechny kalendáře v rozhraní .NET jsou odvozeny z třídy <xref:System.Globalization.Calendar?displayProperty=nameWithType>, která poskytuje základní implementaci kalendáře. Jedna ze tříd, která dědí z třídy <xref:System.Globalization.Calendar>, je <xref:System.Globalization.EastAsianLunisolarCalendar> třída, která je základní třídou pro všechny lunasolární kalendáře. Rozhraní .NET zahrnuje následující implementace kalendáře:

- <xref:System.Globalization.ChineseLunisolarCalendar>, který představuje čínský kalendář lunasolární.

- <xref:System.Globalization.GregorianCalendar>, který představuje gregoriánský kalendář. Tento kalendář je dále rozdělen do podtypů (například arabštiny a Střední východ francouzštiny), které jsou definovány výčtem <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType>. Vlastnost <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> určuje podtyp gregoriánského kalendáře.

- <xref:System.Globalization.HebrewCalendar>, který představuje hebrejský kalendář.

- <xref:System.Globalization.HijriCalendar>, který představuje kalendář hidžra.

- <xref:System.Globalization.JapaneseCalendar>, která představuje japonský kalendář.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, která představuje Japonský lunasolární kalendář.

- <xref:System.Globalization.JulianCalendar>, který představuje juliánské kalendář.

- <xref:System.Globalization.KoreanCalendar>, která představuje korejský kalendář.

- <xref:System.Globalization.KoreanLunisolarCalendar>, která představuje korejský kalendář lunasolární.

- <xref:System.Globalization.PersianCalendar>, který představuje perské kalendář.

- <xref:System.Globalization.TaiwanCalendar>, která představuje Tchajwanský kalendář.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, která představuje tchajwanský lunasolární kalendář.

- <xref:System.Globalization.ThaiBuddhistCalendar>, která představuje thajský buddhistický kalendář.

- <xref:System.Globalization.UmAlQuraCalendar>, který představuje-Qura Kalendář Um.

Kalendář lze použít jedním ze dvou způsobů:

- Jako kalendář, který používá konkrétní jazyková verze. Každý objekt <xref:System.Globalization.CultureInfo> má aktuální kalendář, který je kalendářem, který objekt aktuálně používá. Řetězcové vyjádření hodnot data a času automaticky odrážejí aktuální jazykovou verzi a aktuální kalendář. Aktuálním kalendářem je obvykle výchozí kalendář dané jazykové verze. <xref:System.Globalization.CultureInfo> objekty mají také volitelné kalendáře, které zahrnují další kalendáře, které může jazyková verze používat.

- Jako samostatný kalendář, který není závislý na konkrétní jazykové verzi. V tomto případě se <xref:System.Globalization.Calendar> metody používají k vyjádření kalendářních dat jako hodnot, které odpovídají kalendáři.

Všimněte si, že šest tříd kalendáře – <xref:System.Globalization.ChineseLunisolarCalendar>, <xref:System.Globalization.JapaneseLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>a <xref:System.Globalization.TaiwanLunisolarCalendar> – lze použít pouze jako samostatné kalendáře. Tyto kalendáře nepoužívá žádná jazyková verze jako výchozí kalendář nebo jako volitelný kalendář.

## <a name="calendars-and-cultures"></a>Kalendáře a jazykové verze

Každá jazyková verze má výchozí kalendář, který je definován vlastností <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. Vlastnost <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vrací pole <xref:System.Globalization.Calendar> objektů, které určují všechny kalendáře podporované konkrétní jazykovou verzí, včetně výchozího kalendáře této jazykové verze.

Následující příklad ukazuje vlastnosti <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> a <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Vytvoří `CultureInfo` objekty pro jazykové verze thajštiny (Thajsko) a japonština (Japonsko) a zobrazí jejich výchozí a volitelné kalendáře. Všimněte si, že v obou případech je výchozí kalendář jazykové verze také zahrnut do kolekce <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendář, který aktuálně používá určitý objekt <xref:System.Globalization.CultureInfo>, je definován vlastností <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> jazykové verze. Vlastnost <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vrací objekt <xref:System.Globalization.DateTimeFormatInfo> jazykové verze. Když je vytvořena jazyková verze, její výchozí hodnota je stejná jako hodnota vlastnosti <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType>. Aktuální kalendář jazykové verze však lze změnit na libovolný kalendář obsažený v poli, který je vrácen vlastností <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. Pokud se pokusíte nastavit aktuální kalendář na kalendář, který není zahrnutý do hodnoty vlastnosti <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>, je vyvolána <xref:System.ArgumentException>.

Následující příklad znázorňuje změnu kalendáře používaného jazykovou verzí Arabština (Saúdská Arábie). Nejprve vytvoří instanci <xref:System.DateTime> a zobrazí ji pomocí aktuální jazykové verze – v tomto případě je to angličtina (USA) – a aktuální kalendář jazykové verze (v tomto případě je to gregoriánský kalendář). Poté změní aktuální jazykovou verzi na verzi Arabština (Saúdská Arábie) a zobrazí datum pomocí výchozího kalendáře Um-al-Qura. Pak zavolá metodu `CalendarExists` k určení, zda je kalendář hidžra podporován jazykovou verzí Arabština (Saúdská Arábie). Vzhledem k tomu, že kalendář je podporován, změní aktuální kalendář na kalendář Hidžra a znovu zobrazí datum. V obou případech je datum zobrazeno pomocí aktuálního kalendáře aktuální jazykové verze.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Data a kalendáře

S výjimkou konstruktorů, které obsahují parametr typu <xref:System.Globalization.Calendar> a povolují prvky data (tj. měsíc, den a rok) k tomu, aby odrážely hodnoty v určeném kalendáři, hodnoty <xref:System.DateTime> a <xref:System.DateTimeOffset> jsou vždy založené na gregoriánském kalendáři. To například znamená, že vlastnost <xref:System.DateTime.Year%2A?displayProperty=nameWithType> vrátí rok v gregoriánském kalendáři a vlastnost <xref:System.DateTime.Day%2A?displayProperty=nameWithType> vrátí den v měsíci v gregoriánském kalendáři.

> [!IMPORTANT]
> Je důležité mít na paměti, že existuje rozdíl mezi hodnotou data a řetězcovým vyjádřením tohoto data. První zmíněná položka je založena na gregoriánském kalendáři, druhá zmíněná položka pak vychází z aktuálního kalendáře konkrétní jazykové verze.

Následující příklad ukazuje tento rozdíl mezi vlastnostmi <xref:System.DateTime> a jejich odpovídajícími metodami <xref:System.Globalization.Calendar>. V tomto příkladu je aktuální jazykovou verzí Arabština (Egypt) a aktuální kalendář je Um-al-Qura. Hodnota <xref:System.DateTime> je nastavená na patnáctý den sedmého měsíce v 2011. Je jasné, že je interpretován jako gregoriánské datum, protože tyto stejné hodnoty jsou vráceny metodou <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, když používá konvence invariantní jazykové verze. Řetězcové vyjádření data, které je naformátováno pomocí konvencí aktuální jazykové verze, je 14/08/32, což odpovídá datu v kalendáři Um-al-Qura. Dále jsou pro vrácení dne, měsíce a roku <xref:System.DateTime> hodnoty použity členy `DateTime` a `Calendar`. V každém případě hodnoty vrácené <xref:System.DateTime> členy odráží hodnoty v gregoriánském kalendáři, zatímco hodnoty vrácené <xref:System.Globalization.UmAlQuraCalendar> členy odráží hodnoty v kalendáři Uum Al--Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Vytvoření instance kalendářních dat na základě kalendáře

Vzhledem k tomu, že hodnoty <xref:System.DateTime> a <xref:System.DateTimeOffset> jsou založeny na gregoriánském kalendáři, je nutné volat přetížený konstruktor, který obsahuje parametr typu <xref:System.Globalization.Calendar> pro vytvoření instance hodnoty data, pokud chcete použít hodnoty den, měsíc nebo rok z jiného kalendáře. Můžete také volat jedno z přetížení konkrétního <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> v kalendáři pro vytvoření instance <xref:System.DateTime> objektu na základě hodnot konkrétního kalendáře.

Následující příklad vytvoří instanci jedné <xref:System.DateTime> hodnoty předáním objektu <xref:System.Globalization.HebrewCalendar> do konstruktoru <xref:System.DateTime> a vytvoří instanci druhé <xref:System.DateTime> hodnotu voláním metody <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType>. Vzhledem k tomu, že tyto dvě hodnoty jsou vytvořeny se stejnými hodnotami z hebrejského kalendáře, volání metody <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> ukazuje, že dvě <xref:System.DateTime> hodnoty jsou stejné.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Znázornit data v aktuálním kalendáři

Metoda formátování data a času používá při konverzi dat do řetězců vždy aktuální kalendář. To znamená, že řetězcové vyjádření roku, měsíce a dne v měsíci odpovídá aktuálnímu kalendáři a nemusí nutně zohledňovat gregoriánský kalendář.

Následující příklad znázorňuje vliv aktuálního kalendáře na řetězcové vyjádření data. Nastaví aktuální jazykovou verzi Čínština (tradiční, Tchaj-wan) a vytvoří instanci hodnoty data. Pak zobrazí aktuální kalendář a datum, změní aktuální kalendář na <xref:System.Globalization.TaiwanCalendar>a znovu zobrazí aktuální kalendář a datum. Při prvním zobrazení je datum vyjádřeno jako datum v gregoriánském kalendáři. Při druhém zobrazení je datum vyjádřeno jako datum v tchajwanském kalendáři.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Představuje data v neaktuálním kalendáři.

Chcete-li znázornit datum pomocí kalendáře, který není aktuálním kalendářem konkrétní jazykové verze, je nutné volat metody objektu <xref:System.Globalization.Calendar>. Například metody <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> převádějí rok, měsíc a den na hodnoty, které odpovídají konkrétnímu kalendáři.

> [!WARNING]
> Vzhledem k tomu, že některé kalendáře neobsahují volitelné kalendáře žádné jazykové verze, vyžaduje zobrazení dat v těchto kalendářích vždy volání metod kalendáře. To platí pro všechny kalendáře, které jsou odvozeny z tříd <xref:System.Globalization.EastAsianLunisolarCalendar>, <xref:System.Globalization.JulianCalendar>a <xref:System.Globalization.PersianCalendar>.

Následující příklad používá objekt <xref:System.Globalization.JulianCalendar> k vytvoření instance Date, 9. ledna 1905 v juliánském kalendáři. Pokud je toto datum zobrazeno pomocí výchozího (gregoriánského) kalendáře, má podobu 22. ledna 1905. Volání jednotlivých metod <xref:System.Globalization.JulianCalendar> umožňují, aby datum představovalo v juliánském kalendáři.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendáře a rozsahy dat

Nejdřívější datum, které kalendář podporuje, je označeno vlastností <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> tohoto kalendáře. Pro třídu <xref:System.Globalization.GregorianCalendar> je toto datum 1. ledna 0001 0001 Většina dalších kalendářů v podpoře .NET je pozdější datum. Při pokusu o práci s hodnotou data a času, která předchází nejdřívější podporované datum v kalendáři, vyvolá výjimku <xref:System.ArgumentOutOfRangeException>.

Existuje však jedna důležitá výjimka. Výchozí (neinicializovaná) hodnota objektu <xref:System.DateTime> a objekt <xref:System.DateTimeOffset> je rovna hodnotě <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType>. Pokud se pokusíte naformátovat toto datum v kalendáři, který nepodporuje 1. ledna 0001 0001 a neposkytujete specifikátor formátu, metoda formátování používá specifikátor formátu "s" (seřaditelné schéma data a času) namísto specifikátoru formátu "G" (obecný formát data a času). V důsledku toho operace formátování nevyvolá výjimku <xref:System.ArgumentOutOfRangeException>. Namísto toho vrátí nepodporované datum. To je znázorněno v následujícím příkladu, který zobrazuje hodnotu <xref:System.DateTime.MinValue?displayProperty=nameWithType>, pokud je aktuální jazyková verze nastavena na japonština (Japonsko) s japonským kalendářem a do arabštiny (Egypt) s kalendářem um –-Qura. Nastaví také aktuální jazykovou verzi na angličtinu (USA) a zavolá metodu <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> s každým z těchto objektů <xref:System.Globalization.CultureInfo>. V obou případech je datum zobrazeno pomocí seřaditelného vzorce data/času.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Práce s mazáním

Data v kalendářích jsou obvykle rozdělena do období. Třídy <xref:System.Globalization.Calendar> v rozhraní .NET však nepodporují každé období definované kalendářem a většina tříd <xref:System.Globalization.Calendar> podporuje pouze jedno období. Pouze třídy <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar> podporují více mazání.

> [!IMPORTANT]
> Reiwa období, nové období v <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>začíná 1. května 2019. Tato změna má vliv na všechny aplikace, které používají tyto kalendáře. Další informace najdete v následujících článcích:
>
> - [Zpracování nového období v japonském kalendáři v rozhraní .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), který obsahuje funkce přidané do .NET pro podporu kalendářů s více nástroji pro mazání a popisuje osvědčené postupy pro použití při zpracování kalendářů s více obdobími.
> - [Připravte svoji aplikaci na změnu v japonském období](/windows/uwp/design/globalizing/japanese-era-change), která poskytuje informace o testování vašich aplikací ve Windows, aby se zajistila jejich připravenost na změnu období.
> - [Shrnutí nových aktualizací pro .NET Framework v rámci japonského období](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), které obsahují .NET Framework aktualizace pro jednotlivé verze Windows, které se vztahují k novému japonskému období, poznamenejte si nové .NET Framework funkce pro podporu více období a zahrnete do testování vašich aplikací věci, které byste měli hledat.

Období ve většině kalendářních prostředí označuje extrémně dlouhou dobu. V gregoriánském kalendáři například aktuální období zahrnuje více než dvě MILLENNIA. Pro <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>se jedná o dva kalendáře, které podporují více mazání. Období odpovídá období reignu císaře. Podpora vícenásobného mazání, zejména pokud je horní limit aktuálního období neznámý, přináší zvláštní výzvy.

### <a name="eras-and-era-names"></a>Názvy pro mazání a období

V rozhraní .NET jsou celá čísla, která představují mazání podporovaná implementací konkrétního kalendáře, ukládána v opačném pořadí v poli <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType>. Aktuální období (což je období s nejpozdějším časovým rozsahem) je index nula a pro <xref:System.Globalization.Calendar> třídy, které podporují více než jednou, každý postupný index odráží předchozí období. Vlastnost Static <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> definuje index aktuálního období v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType>m poli. je konstanta, jejíž hodnota je vždycky nula. Jednotlivé třídy <xref:System.Globalization.Calendar> také obsahují statická pole, která vracejí hodnotu aktuálního období. Jsou uvedeny v následující tabulce.

| Třída kalendáře                                        | Pole aktuálního období                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

Název, který odpovídá určitému číslu období, lze načíst předáním čísla období do <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> metody. Následující příklad volá tyto metody pro načtení informací o podpoře prostředí ve třídě <xref:System.Globalization.GregorianCalendar>. Zobrazuje datum gregoriánského kalendáře, které odpovídá 1. lednu v aktuálním období, a také datum gregoriánského kalendáře, které odpovídá 1. lednu každého podporovaného období japonského kalendáře.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Vytvoření instance a data pomocí období

Pro dvě <xref:System.Globalization.Calendar> třídy, které podporují více mazání, může být datum, které se skládá z konkrétního roku, měsíce a dne v hodnotě měsíce, nejednoznačné. Například všechna mazání podporovaná <xref:System.Globalization.JapaneseCalendar> mají roky, jejichž číslo je 1. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. To platí pro <xref:System.DateTime.%23ctor%2A> a <xref:System.DateTimeOffset.%23ctor%2A> konstruktory, které zahrnují parametry typu <xref:System.Globalization.Calendar>a také metody [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) a [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) . V následujícím příkladu je vytvořena instance data, která představuje 1. ledna v nespecifikovaném období. Pokud tento příklad spustíte, pokud je Reiwa období aktuálním obdobím, datum se interpretuje jako druhý rok období Reiwa. Období 令和 předchází roku v řetězci vráceném metodou <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> a odpovídá 1. ledna 2020 v gregoriánském kalendáři. (Období Reiwa začíná v roce 2019 gregoriánského kalendáře.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Pokud se však změní období, záměr tohoto kódu se změní na nejednoznačný. Je datum, které má představovat druhý rok aktuálního období, nebo je určeno k vyjádření druhého roku Heisei období? Existují dva způsoby, jak se vyhnout této nejednoznačné možnosti:

- Vytvoří instanci hodnoty data a času pomocí výchozí <xref:System.Globalization.GregorianCalendar> třídy. Pak můžete použít japonský kalendář nebo Japonský lunasolární kalendář pro řetězcové vyjádření kalendářních dat, jak ukazuje následující příklad.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Zavolejte metodu data a času, která explicitně určuje období. To zahrnuje následující metody:

  - Metoda <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> třídy <xref:System.Globalization.JapaneseCalendar> nebo <xref:System.Globalization.JapaneseLunisolarCalendar>

  - Metoda analýzy <xref:System.DateTime> nebo <xref:System.DateTimeOffset>, například <xref:System.DateTime.Parse%2A>, <xref:System.DateTime.TryParse%2A>, <xref:System.DateTime.ParseExact%2A>nebo <xref:System.DateTime.TryParseExact%2A>, která obsahuje řetězec, který má být analyzován, a volitelně také <xref:System.Globalization.DateTimeStyles> argument, pokud je aktuální jazyková verze Japonsko-Japonsko ("ja-JP") a kalendář této jazykové verze je <xref:System.Globalization.JapaneseCalendar>. Řetězec, který se má analyzovat, musí zahrnovat období.

  - Metoda analýzy <xref:System.DateTime> nebo <xref:System.DateTimeOffset>, která obsahuje parametr `provider` typu <xref:System.IFormatProvider>. `provider` musí být buď objekt <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi Japanese-Japonsko ("ja-JP"), jejíž aktuální kalendář je <xref:System.Globalization.JapaneseCalendar>, nebo objekt <xref:System.Globalization.DateTimeFormatInfo>, jehož vlastnost <xref:System.Globalization.DateTimeFormatInfo.Calendar> je <xref:System.Globalization.JapaneseCalendar>. Řetězec, který se má analyzovat, musí zahrnovat období.

  Následující příklad používá tři tyto metody k vytvoření instance data a času v Meiji období, od 8. září 1868 a skončila 29. července 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Při práci s kalendáři, které podporují více mazání, *vždy* použijte gregoriánské datum k vytvoření instance data nebo při vytváření instance data a času založeného na daném kalendáři určete období.

V části určení období pro metodu <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> zadáte index období do vlastnosti <xref:System.Globalization.Calendar.Eras> kalendáře. Pro kalendáře, jejichž mazání se může změnit, ale tyto indexy nejsou konstantní hodnoty; aktuální období je v indexu 0 a nejstarší období je v indexu `Eras.Length - 1`. Při přidání nového období do kalendáře se indexy předchozího mazání navzájem zvyšují o jednu. Vhodný index období můžete dodat následujícím způsobem:

- U kalendářních dat v aktuálním období vždy použijte vlastnost <xref:System.Globalization.Calendar.CurrentEra> kalendáře.

- Pro kalendářní data v zadaném období použijte metodu <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> k načtení indexu, který odpovídá zadanému názvu období. To vyžaduje, aby <xref:System.Globalization.JapaneseCalendar> být aktuálním kalendářem <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi ja-JP.  (Tato technika funguje i pro <xref:System.Globalization.JapaneseLunisolarCalendar>, protože podporuje stejnou funkci mazání jako <xref:System.Globalization.JapaneseCalendar>.) Předchozí příklad ukazuje tento přístup.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendáře, mazání a rozsahy dat: odlehčené kontroly rozsahu

Podobně jako jednotlivé kalendáře podporují rozsahy dat, mazání v <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>ch třídách má také podporované rozsahy. Dřív používala technologie .NET striktní kontroly rozsahu období, aby se zajistilo, že datum specifické pro období spadá do rozsahu tohoto období. To znamená, že pokud je datum mimo rozsah zadaného období, vyvolá metoda <xref:System.ArgumentOutOfRangeException>. V současné době .NET používá ve výchozím nastavení odlehčené kontroly rozsahu. Aktualizace všech verzí .NET přináší odlehčené kontroly rozsahu období; pokus o vytvoření instance data specifického pro období, který je mimo rozsah zadaného období, je převedená do následujícího období a nevyvolá se žádná výjimka.

Následující příklad se pokusí vytvořit instanci data v 65th roce Showa období, od 25. prosince 1926 a skončila 7. ledna 1989. Toto datum odpovídá 9. ledna 1990, který je mimo rozsah Showa období v <xref:System.Globalization.JapaneseCalendar>. Jak ukazuje výstup z příkladu, datum zobrazené v příkladu je 9. ledna 1990 v druhém roce Heisei období.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Pokud jsou nespolehlivé kontroly rozsahu nežádoucí, můžete obnovit striktní kontroly rozsahu mnoha různými způsoby v závislosti na verzi rozhraní .NET, na které je aplikace spuštěná:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** V souboru *App. config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE \Software\Microsoft\\. NETFramework\AppContext** |
   | **Jméno** | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   | **Typ** | REG_SZ |
   | **Hodnota** | true |

U povolených striktních kontrol rozsahu vyvolá předchozí příklad <xref:System.ArgumentOutOfRangeException> a zobrazí následující výstup:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Znázornit data v kalendářích s vícenásobným smazáním

Pokud objekt <xref:System.Globalization.Calendar> podporuje mazání a je aktuálním kalendářem <xref:System.Globalization.CultureInfo> objektu, je období zahrnuto v řetězcové reprezentaci hodnoty data a času pro vzor úplného data a času, dlouhého data a krátkého data. Následující příklad zobrazuje tyto vzorce dat, kdy je nastavena aktuální jazyková verze Japonština (Japonsko) a aktuálním kalendářem je japonský kalendář.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Třída <xref:System.Globalization.JapaneseCalendar> je jedinou třídou kalendáře v rozhraní .NET, která podporuje data ve více než jednom období a může být aktuálním kalendářem <xref:System.Globalization.CultureInfo> objektu – konkrétně objektu <xref:System.Globalization.CultureInfo>, který představuje japonskou (Japonsko) jazykovou verzi.

Specifikátor vlastního formátu „o“ zahrnuje období ve výsledném řetězci všech kalendářů. Následující příklad používá vlastní řetězec formátu „MM-dd-rrrr g“ pro vyjádření období ve výsledném řetězci, pokud je aktuální kalendář nastaven na gregoriánský kalendář.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

V případech, kdy je řetězcová reprezentace data vyjádřena v kalendáři, který není aktuálním kalendářem, třída <xref:System.Globalization.Calendar> zahrnuje <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> metodu, kterou lze použít společně s metodami <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> pro jednoznačné označení data a období, ke kterému patří. Následující příklad používá třídu <xref:System.Globalization.JapaneseLunisolarCalendar> k poskytnutí obrázku. Všimněte si však, že pro období ve výsledném řetězci, který obsahuje smysluplný název nebo zkratku namísto celého čísla pro období, vyžaduje vytvoření instance <xref:System.Globalization.DateTimeFormatInfo>ho objektu a <xref:System.Globalization.JapaneseCalendar> jeho aktuálního kalendáře. (<xref:System.Globalization.JapaneseLunisolarCalendar> kalendář nemůže být aktuálním kalendářem žádné jazykové verze, ale v tomto případě dva kalendáře sdílejí stejné mazání.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

V japonských kalendářích se první rok období posuzování označuje jako Gannen (元年). Například místo Heisei 1 se první rok období Heisei dá popsat jako Heisei Gannen. Rozhraní .NET přijme tuto úmluvu v operacích formátování pro data a časy formátované pomocí následujících standardních nebo vlastních formátovacích řetězců pro datum a čas, když se používají s objektem <xref:System.Globalization.CultureInfo>, který představuje jazykovou verzi Japanese-Japonsko ("ja-JP") s třídou <xref:System.Globalization.JapaneseCalendar>:

- [Vzor dlouhého data](../base-types/standard-date-and-time-format-strings.md#LongDate), který je označen řetězcem standardního formátu data a času "D".
- [Vzor úplného formátu data a dlouhého času](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), který je označen řetězcem standardního formátu data a času "F".
- [Vzor úplného data krátkého času](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), který je označen standardním řetězcem formátu data a času "f".
- [Vzor pro rok/měsíc](../base-types/standard-date-and-time-format-strings.md#YearMonth), který je označen řetězcem standardního formátu data a času y nebo y.
- ["GGY" 年 "" nebo "ggy年" [vlastní řetězec formátu data a času](../base-types/custom-date-and-time-format-strings.md).

Například následující příklad zobrazuje datum v prvním roce Heisei období v <xref:System.Globalization.JapaneseCalendar>.

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Pokud je toto chování nežádoucí při formátování operací, můžete obnovit předchozí chování, které vždy představuje první rok v období od "1" místo "Gannen", a to v závislosti na verzi rozhraní .NET:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** V souboru *App. config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE \Software\Microsoft\\. NETFramework\AppContext** |
   | **Jméno** | Switch. System. Globalization. FormatJapaneseFirstYearAsANumber |
   | **Typ** | REG_SZ |
   | **Hodnota** | true |

V případě, že je podpora Gannen v případě zakázaných operací formátování, předchozí příklad zobrazí následující výstup:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

Rozhraní .NET bylo také aktualizováno, aby operace analýzy data a času podporovaly řetězce, které obsahují rok reprezentovaný buď 1 nebo Gannen. I když byste to neměli potřebovat, můžete obnovit předchozí chování a rozpoznává pouze "1" jako první rok období. To lze provést následujícím způsobem v závislosti na verzi rozhraní .NET:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** V souboru *App. config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Key** | **HKEY_LOCAL_MACHINE \Software\Microsoft\\. NETFramework\AppContext** |
   | **Jméno** | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   | **Typ** | REG_SZ |
   | **Hodnota** | true |

## <a name="see-also"></a>Viz také:

- [Postupy: zobrazení dat v jiných než gregoriánského kalendáři](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Ukázka: nástroj rozsah týdne kalendáře](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Calendar – Třída](xref:System.Globalization.Calendar)
