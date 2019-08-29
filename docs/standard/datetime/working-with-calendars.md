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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e92d5564308d31609b9fb024f3d3368a19b76b1d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106704"
---
# <a name="working-with-calendars"></a>Práce s kalendáři

Ačkoli hodnoty data a času představují konkrétní časový okamžik, je řetězcové vyjádření závislé na jazykové verzi a závisí jak na konvencích použitých k zobrazení hodnoty data a času podle konkrétní jazykové verze, tak na kalendáři používaném danou jazykovou verzí. Toto téma popisuje podporu pro kalendáře v rozhraní .NET a popisuje použití tříd kalendáře při práci s hodnotami data.

## <a name="calendars-in-net"></a>Kalendáře v .NET

Všechny kalendáře v rozhraní .NET jsou odvozeny z <xref:System.Globalization.Calendar?displayProperty=nameWithType> třídy, která poskytuje implementaci základního kalendáře. Jedna z tříd, která dědí z <xref:System.Globalization.Calendar> třídy, <xref:System.Globalization.EastAsianLunisolarCalendar> je třída, která je základní třídou pro všechny lunasolární kalendáře. Rozhraní .NET zahrnuje následující implementace kalendáře:

- <xref:System.Globalization.ChineseLunisolarCalendar>, který představuje čínský lunasolární kalendář.

- <xref:System.Globalization.GregorianCalendar>, který představuje gregoriánský kalendář. Tento kalendář je dále rozdělen na podtypy (například arabština a Střední východ francouzštiny), které jsou definovány <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> výčtem. <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> Vlastnost určuje podtyp gregoriánského kalendáře.

- <xref:System.Globalization.HebrewCalendar>, který představuje hebrejský kalendář.

- <xref:System.Globalization.HijriCalendar>, který představuje kalendář hidžra.

- <xref:System.Globalization.JapaneseCalendar>, který představuje japonský kalendář.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, který představuje Japonský lunasolární kalendář.

- <xref:System.Globalization.JulianCalendar>, který představuje juliánské kalendář.

- <xref:System.Globalization.KoreanCalendar>, který představuje korejský kalendář.

- <xref:System.Globalization.KoreanLunisolarCalendar>, který představuje korejský lunasolární kalendář.

- <xref:System.Globalization.PersianCalendar>, který představuje perské kalendář.

- <xref:System.Globalization.TaiwanCalendar>, který představuje Tchajwanský kalendář.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, který představuje tchajwanský lunasolární kalendář.

- <xref:System.Globalization.ThaiBuddhistCalendar>, který představuje thajský buddhistický kalendář.

- <xref:System.Globalization.UmAlQuraCalendar>, který představuje kalendářní Kalendář Um Al-Qura.

Kalendář lze použít jedním ze dvou způsobů:

- Jako kalendář, který používá konkrétní jazyková verze. Každý <xref:System.Globalization.CultureInfo> objekt má aktuální kalendář, což je kalendář, který objekt aktuálně používá. Řetězcové vyjádření hodnot data a času automaticky odrážejí aktuální jazykovou verzi a aktuální kalendář. Aktuálním kalendářem je obvykle výchozí kalendář dané jazykové verze. <xref:System.Globalization.CultureInfo>objekty mají také volitelné kalendáře, které zahrnují další kalendáře, které může jazyková verze používat.

- Jako samostatný kalendář, který není závislý na konkrétní jazykové verzi. V tomto případě <xref:System.Globalization.Calendar> jsou metody použity pro vyjádření kalendářních dat jako hodnoty, které odpovídají kalendáři.

Všimněte si, že šest tříd <xref:System.Globalization.ChineseLunisolarCalendar>kalendáře <xref:System.Globalization.JapaneseLunisolarCalendar>– <xref:System.Globalization.JulianCalendar>, <xref:System.Globalization.KoreanLunisolarCalendar>, <xref:System.Globalization.PersianCalendar>,, <xref:System.Globalization.TaiwanLunisolarCalendar> a – lze použít pouze jako samostatné kalendáře. Tyto kalendáře nepoužívá žádná jazyková verze jako výchozí kalendář nebo jako volitelný kalendář.

## <a name="calendars-and-cultures"></a>Kalendáře a jazykové verze

Každá jazyková verze má výchozí kalendář, který je definován <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastností. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Vlastnost vrací<xref:System.Globalization.Calendar> pole objektů, které určují všechny kalendáře podporované konkrétní jazykovou verzí, včetně výchozího kalendáře této jazykové verze.

Následující příklad ilustruje <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> . Vytvoří `CultureInfo` objekty pro jazykové verze thajštiny (Thajsko) a japonština (Japonsko) a zobrazí jejich výchozí a volitelné kalendáře. Všimněte si, že v obou případech je výchozí kalendář jazykové verze také zahrnut do <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekce.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendář, který je aktuálně používán konkrétním <xref:System.Globalization.CultureInfo> objektem, je definován <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastností jazykové verze. <xref:System.Globalization.DateTimeFormatInfo> Objekt jazykové verze je vrácen <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností. Když je vytvořena jazyková verze, její výchozí hodnota je stejná jako hodnota <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnosti. Aktuální kalendář jazykové verze však lze změnit na libovolný kalendář obsažený v poli, který je <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vrácen vlastností. Pokud se pokusíte nastavit aktuální kalendář na kalendář, který není zahrnutý v <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> hodnotě vlastnosti <xref:System.ArgumentException> , je vyvolána výjimka.

Následující příklad znázorňuje změnu kalendáře používaného jazykovou verzí Arabština (Saúdská Arábie). Nejprve vytvoří instanci <xref:System.DateTime> hodnoty a zobrazí ji pomocí aktuální jazykové verze – to znamená, že v tomto případě je to angličtina (USA) – a aktuální kalendář jazykové verze (v tomto případě je to gregoriánský kalendář). Poté změní aktuální jazykovou verzi na verzi Arabština (Saúdská Arábie) a zobrazí datum pomocí výchozího kalendáře Um-al-Qura. Poté volá `CalendarExists` metodu k určení, zda je kalendář hidžra podporován jazykovou verzí Arabština (Saúdská Arábie). Vzhledem k tomu, že kalendář je podporován, změní aktuální kalendář na kalendář Hidžra a znovu zobrazí datum. V obou případech je datum zobrazeno pomocí aktuálního kalendáře aktuální jazykové verze.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Data a kalendáře

S výjimkou konstruktorů, které obsahují parametr typu <xref:System.Globalization.Calendar> a umožňují prvky data (tj. měsíc, den a rok), aby odrážely hodnoty v určeném kalendáři <xref:System.DateTime> , hodnoty a <xref:System.DateTimeOffset> jsou vždy na základě gregoriánského kalendáře. To znamená, že <xref:System.DateTime.Year%2A?displayProperty=nameWithType> vlastnost například vrátí rok v gregoriánském kalendáři <xref:System.DateTime.Day%2A?displayProperty=nameWithType> a vlastnost vrátí den v měsíci v gregoriánském kalendáři.

> [!IMPORTANT]
> Je důležité mít na paměti, že existuje rozdíl mezi hodnotou data a řetězcovým vyjádřením tohoto data. První zmíněná položka je založena na gregoriánském kalendáři, druhá zmíněná položka pak vychází z aktuálního kalendáře konkrétní jazykové verze.

Následující příklad znázorňuje tento rozdíl mezi <xref:System.DateTime> vlastnostmi a jejich odpovídajícími <xref:System.Globalization.Calendar> metodami. V tomto příkladu je aktuální jazykovou verzí Arabština (Egypt) a aktuální kalendář je Um-al-Qura. <xref:System.DateTime> Hodnota je nastavená na patnáctý den sedmého měsíce z 2011. Je jasné, že je interpretován jako gregoriánské datum, protože tyto stejné hodnoty jsou vráceny <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodou, když používá konvence invariantní jazykové verze. Řetězcové vyjádření data, které je naformátováno pomocí konvencí aktuální jazykové verze, je 14/08/32, což odpovídá datu v kalendáři Um-al-Qura. Dále jsou členy `DateTime` a `Calendar` použity k vrácení dne, měsíce <xref:System.DateTime> a roku hodnoty. V každém případě hodnoty vrácené <xref:System.DateTime> členy odrážejí hodnoty v gregoriánském kalendáři, zatímco hodnoty <xref:System.Globalization.UmAlQuraCalendar> vrácené členy představují hodnoty v kalendáři Uum Al--Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>Vytváření instancí kalendářních dat na základě kalendáře

Vzhledem <xref:System.DateTime> k <xref:System.DateTimeOffset> tomu, že hodnoty a jsou založeny na gregoriánském kalendáři, je nutné volat přetížený konstruktor, který obsahuje parametr typu <xref:System.Globalization.Calendar> pro vytvoření instance hodnoty data, pokud chcete použít hodnoty den, měsíc nebo rok z jiný kalendář. Můžete také volat jedno z přetížení <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> metody konkrétního kalendáře pro vytvoření instance <xref:System.DateTime> objektu založeného na hodnotách konkrétního kalendáře.

Následující příklad vytvoří instanci jedné <xref:System.DateTime> hodnoty <xref:System.Globalization.HebrewCalendar> předáním objektu <xref:System.DateTime> konstruktoru a <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> instanci druhé <xref:System.DateTime> hodnoty voláním metody. Vzhledem k <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> tomu, že tyto dvě hodnoty jsou vytvořeny se stejnými hodnotami z hebrejského kalendáře, volání metody ukazuje, <xref:System.DateTime> že dvě hodnoty jsou stejné.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>Reprezentace dat v aktuálním kalendáři

Metoda formátování data a času používá při konverzi dat do řetězců vždy aktuální kalendář. To znamená, že řetězcové vyjádření roku, měsíce a dne v měsíci odpovídá aktuálnímu kalendáři a nemusí nutně zohledňovat gregoriánský kalendář.

Následující příklad znázorňuje vliv aktuálního kalendáře na řetězcové vyjádření data. Nastaví aktuální jazykovou verzi Čínština (tradiční, Tchaj-wan) a vytvoří instanci hodnoty data. Pak zobrazí aktuální kalendář a datum, změní aktuální kalendář na <xref:System.Globalization.TaiwanCalendar>a zobrazí aktuální kalendář a datum znovu. Při prvním zobrazení je datum vyjádřeno jako datum v gregoriánském kalendáři. Při druhém zobrazení je datum vyjádřeno jako datum v tchajwanském kalendáři.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>Reprezentace dat v neaktuálním kalendáři

Chcete-li znázornit datum pomocí kalendáře, který není aktuálním kalendářem konkrétní jazykové verze, je nutné volat metody <xref:System.Globalization.Calendar> tohoto objektu. Například <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>metody, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> převádějí rok, měsíc a den na hodnoty, které odpovídají konkrétnímu kalendáři.

> [!WARNING]
> Vzhledem k tomu, že některé kalendáře neobsahují volitelné kalendáře žádné jazykové verze, vyžaduje zobrazení dat v těchto kalendářích vždy volání metod kalendáře. To platí pro všechny kalendáře, které jsou odvozeny <xref:System.Globalization.EastAsianLunisolarCalendar>z <xref:System.Globalization.JulianCalendar>tříd, <xref:System.Globalization.PersianCalendar> a.

Následující příklad používá <xref:System.Globalization.JulianCalendar> objekt pro vytvoření instance Date, 9. ledna 1905 v juliánském kalendáři. Pokud je toto datum zobrazeno pomocí výchozího (gregoriánského) kalendáře, má podobu 22. ledna 1905. Volání jednotlivých <xref:System.Globalization.JulianCalendar> metod umožní znázornit datum v juliánském kalendáři.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendáře a rozsahy dat

Nejdřívější datum, které kalendář podporuje, je označeno <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> vlastností tohoto kalendáře. <xref:System.Globalization.GregorianCalendar> Pro třídu je toto datum 1. ledna 0001 0001 Většina dalších kalendářů v podpoře .NET je pozdější datum. Při pokusu o práci s hodnotou data a času, která předchází nejdřívější podporované datum kalendáře, <xref:System.ArgumentOutOfRangeException> vyvolá výjimku.

Existuje však jedna důležitá výjimka. Výchozí (neinicializovaná) hodnota <xref:System.DateTime> objektu <xref:System.DateTimeOffset> a <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> objektu je rovna hodnotě. Pokud se pokusíte naformátovat toto datum v kalendáři, který nepodporuje 1. ledna 0001 0001 a neposkytujete specifikátor formátu, metoda formátování používá specifikátor formátu "s" (seřaditelné schéma data a času) namísto specifikátoru formátu "G" (obecný formát data a času). V důsledku toho operace formátování nevyvolá <xref:System.ArgumentOutOfRangeException> výjimku. Namísto toho vrátí nepodporované datum. To je znázorněno v následujícím příkladu, který zobrazuje hodnotu <xref:System.DateTime.MinValue?displayProperty=nameWithType> , když je aktuální jazyková verze nastavena na japonština (Japonsko) s japonským kalendářem a do arabštiny (Egypt) s-quram kalendáře pro um. Také nastaví aktuální jazykovou verzi na angličtinu (USA) a volá <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> metodu s každým z těchto <xref:System.Globalization.CultureInfo> objektů. V obou případech je datum zobrazeno pomocí seřaditelného vzorce data/času.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>Práce s mazáním

Data v kalendářích jsou obvykle rozdělena do období. Třídy v rozhraní .NET však nepodporují každé období definované kalendářem a většina <xref:System.Globalization.Calendar> tříd podporuje pouze jedno období. <xref:System.Globalization.Calendar> Pouze třídy <xref:System.Globalization.JapaneseLunisolarCalendar> a podporují více mazání. <xref:System.Globalization.JapaneseCalendar>

> [!IMPORTANT]
> Reiwa období, nové období v <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>, začíná 1. května 2019. Tato změna má vliv na všechny aplikace, které používají tyto kalendáře. Další informace najdete v následujících článcích:
> - [Zpracování nového období v japonském kalendáři v rozhraní .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), který obsahuje funkce přidané do .NET pro podporu kalendářů s více nástroji pro mazání a popisuje osvědčené postupy pro použití při zpracování kalendářů s více obdobími.
> - [Připravte svoji aplikaci na změnu v japonském období](/windows/uwp/design/globalizing/japanese-era-change), která poskytuje informace o testování vašich aplikací ve Windows, aby se zajistila jejich připravenost na změnu období.
> - [Shrnutí nových aktualizací pro .NET Framework v rámci japonského období](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), které obsahují .NET Framework aktualizace pro jednotlivé verze systému Windows, které se vztahují k novému japonskému období v japonštině, poznamenejte si nové .NET Framework funkce pro podporu více období a zahrnuje věci Vyhledejte v testování vašich aplikací.

Období ve většině kalendářních prostředí označuje extrémně dlouhou dobu. V gregoriánském kalendáři například aktuální období zahrnuje více než dvě MILLENNIA. <xref:System.Globalization.JapaneseCalendar> Pro<xref:System.Globalization.JapaneseLunisolarCalendar>a, dva kalendáře, které podporují více mazání, to není případ. Období odpovídá období reignu císaře. Podpora vícenásobného mazání, zejména pokud je horní limit aktuálního období neznámý, přináší zvláštní výzvy.

### <a name="eras-and-era-names"></a>Názvy pro mazání a období

V rozhraní .NET jsou celá čísla, která představují mazání podporovaná implementací konkrétního kalendáře, ukládána v opačném pořadí v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> poli. Aktuální období (což je období s nejpozdějším časovým rozsahem) je index nula a pro <xref:System.Globalization.Calendar> třídy, které podporují více mazání, každý úspěšný index odráží předchozí období. Statická <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> vlastnost definuje index aktuálního období <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> v poli; je konstanta, jejíž hodnota je vždy nula. Jednotlivé <xref:System.Globalization.Calendar> třídy také obsahují statická pole, která vracejí hodnotu aktuálního období. Jsou uvedeny v následující tabulce.

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

Název, který odpovídá určitému číslu období, lze načíst předáním čísla období do <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metody nebo. <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> Následující příklad volá tyto metody pro načtení informací o podpoře prostředí ve <xref:System.Globalization.GregorianCalendar> třídě. Zobrazuje datum gregoriánského kalendáře, které odpovídá 1. lednu v aktuálním období, a také datum gregoriánského kalendáře, které odpovídá 1. lednu každého podporovaného období japonského kalendáře.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace naleznete v tématu [Vlastní řetězce formátu data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiating-a-date-with-an-era"></a>Vytvoření instance data s obdobím

Pro dvě <xref:System.Globalization.Calendar> třídy, které podporují více mazání, může být datum, které se skládá z konkrétního roku, měsíce a dne v hodnotě měsíce, nejednoznačné. Například všechny mazání, které podporuje, <xref:System.Globalization.JapaneseCalendar> jsou roky, jejichž počet je 1. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. <xref:System.DateTime.%23ctor%2A> To platí pro konstruktory a <xref:System.DateTimeOffset.%23ctor%2A> , které obsahují parametry typu <xref:System.Globalization.Calendar>, a také metody [JapaneseCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) a [JapaneseLunisolarCalendar. ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) . V následujícím příkladu je vytvořena instance data, která představuje 1. ledna v nespecifikovaném období. Pokud tento příklad spustíte, pokud je Reiwa období aktuálním obdobím, datum se interpretuje jako druhý rok období Reiwa. Období 令和 předchází roku v řetězci vráceném <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> metodou a odpovídá 1. ledna 2020 v gregoriánském kalendáři. (Období Reiwa začíná v roce 2019 gregoriánského kalendáře.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Pokud se však změní období, záměr tohoto kódu se změní na nejednoznačný. Je datum, které má představovat druhý rok aktuálního období, nebo je určeno k vyjádření druhého roku Heisei období? Existují dva způsoby, jak se vyhnout této nejednoznačné možnosti:

- Vytvoří instanci hodnoty data a času pomocí výchozí <xref:System.Globalization.GregorianCalendar> třídy. Pak můžete použít japonský kalendář nebo Japonský lunasolární kalendář pro řetězcové vyjádření kalendářních dat, jak ukazuje následující příklad.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Zavolejte metodu data a času, která explicitně určuje období. To zahrnuje následující metody:

  - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> Metoda<xref:System.Globalization.JapaneseCalendar> třídy or .<xref:System.Globalization.JapaneseLunisolarCalendar>

  - Metodanebo<xref:System.DateTimeOffset>, například <xref:System.DateTime.Parse%2A> ,,<xref:System.DateTime.TryParseExact%2A>,nebo, která obsahuje řetězec, který má být analyzován, a volitelně argument,pokudjeaktuálníjazykováverzejaponština-Japonsko("<xref:System.Globalization.DateTimeStyles> <xref:System.DateTime.ParseExact%2A> <xref:System.DateTime.TryParse%2A> <xref:System.DateTime> ja-JP ") a v <xref:System.Globalization.JapaneseCalendar>kalendáři jazykové verze je. Řetězec, který se má analyzovat, musí zahrnovat období.

  - Metoda <xref:System.DateTime> nebo <xref:System.DateTimeOffset> Analýza,která<xref:System.IFormatProvider>obsahuje parametr typu. `provider` `provider`musí <xref:System.Globalization.CultureInfo> být buď objekt, který představuje jazykovou verzi japonského Japonska ("ja-jp"), jejíž aktuální <xref:System.Globalization.JapaneseCalendar> kalendář je <xref:System.Globalization.DateTimeFormatInfo> nebo objekt <xref:System.Globalization.DateTimeFormatInfo.Calendar> , jehož <xref:System.Globalization.JapaneseCalendar>vlastnost je. Řetězec, který se má analyzovat, musí zahrnovat období.

  Následující příklad používá tři tyto metody k vytvoření instance data a času v Meiji období, od 8. září 1868 a skončila 29. července 1912.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Při práci s kalendáři, které podporují více mazání, *vždy* použijte gregoriánské datum k vytvoření instance data nebo při vytváření instance data a času založeného na daném kalendáři určete období.

V části určení období pro <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metodu zadejte index období ve <xref:System.Globalization.Calendar.Eras> vlastnosti kalendáře. Pro kalendáře, jejichž mazání se může změnit, ale tyto indexy nejsou konstantní hodnoty; aktuální období je v indexu 0 a nejstarší období je v indexu `Eras.Length - 1`. Při přidání nového období do kalendáře se indexy předchozího mazání navzájem zvyšují o jednu. Vhodný index období můžete dodat následujícím způsobem:

- U kalendářních dat v aktuálním období používejte vždy <xref:System.Globalization.Calendar.CurrentEra> vlastnost Calendar.

- Pro kalendářní data v zadaném období použijte <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> metodu k načtení indexu, který odpovídá zadanému názvu období. To vyžaduje, aby <xref:System.Globalization.JapaneseCalendar> byl aktuální kalendář <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi ja-JP.  (Tato technika funguje <xref:System.Globalization.JapaneseLunisolarCalendar> i v případě, že podporuje stejné mazání <xref:System.Globalization.JapaneseCalendar>jako.) Předchozí příklad ukazuje tento přístup.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendáře, mazání a rozsahy dat: Odlehčené kontroly rozsahu

Podobně jako jednotlivé kalendáře podporují rozsahy dat, mazání v <xref:System.Globalization.JapaneseCalendar> třídách a <xref:System.Globalization.JapaneseLunisolarCalendar> také má podporované rozsahy. Dřív používala technologie .NET striktní kontroly rozsahu období, aby se zajistilo, že datum specifické pro období spadá do rozsahu tohoto období. To znamená, že pokud je datum mimo rozsah určeného období, metoda vyvolá <xref:System.ArgumentOutOfRangeException>. V současné době .NET používá ve výchozím nastavení odlehčené kontroly rozsahu. Aktualizace všech verzí .NET přináší odlehčené kontroly rozsahu období; pokus o vytvoření instance data specifického pro období, který je mimo rozsah zadaného období, je převedená do následujícího období a nevyvolá se žádná výjimka.

Následující příklad se pokusí vytvořit instanci data v 65th roce Showa období, od 25. prosince 1926 a skončila 7. ledna 1989. Toto datum odpovídá 9. ledna 1990, který je mimo rozsah Showa období v <xref:System.Globalization.JapaneseCalendar>. Jak ukazuje výstup z příkladu, datum zobrazené v příkladu je 9. ledna 1990 v druhém roce Heisei období.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Pokud jsou nespolehlivé kontroly rozsahu nežádoucí, můžete obnovit striktní kontroly rozsahu mnoha různými způsoby v závislosti na verzi rozhraní .NET, na které je aplikace spuštěná:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* můžete přidat následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** Můžete nastavit následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Name | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |type | REG_SZ |
   |Value | true |

Při povolených striktních kontrolách rozsahu vyvolá <xref:System.ArgumentOutOfRangeException> předchozí příklad příkaz a zobrazí následující výstup:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>Reprezentace dat v kalendářích s vícenásobným smazáním

Pokud objekt podporuje mazání a je aktuálním kalendářem <xref:System.Globalization.CultureInfo> objektu, je období zahrnuto v řetězcové reprezentaci hodnoty data a času pro vzor úplného data a času, dlouhého data a krátkého data. <xref:System.Globalization.Calendar> Následující příklad zobrazuje tyto vzorce dat, kdy je nastavena aktuální jazyková verze Japonština (Japonsko) a aktuálním kalendářem je japonský kalendář.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Třída je jedinou třídou kalendáře v rozhraní .NET, která podporuje data ve více než jednom období a může být aktuální kalendář <xref:System.Globalization.CultureInfo> objektu <xref:System.Globalization.CultureInfo> – konkrétně objekt, který představuje japonské (Japonsko) jazykovou verzi. <xref:System.Globalization.JapaneseCalendar>

Specifikátor vlastního formátu „o“ zahrnuje období ve výsledném řetězci všech kalendářů. Následující příklad používá vlastní řetězec formátu „MM-dd-rrrr g“ pro vyjádření období ve výsledném řetězci, pokud je aktuální kalendář nastaven na gregoriánský kalendář.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

V případech, kdy řetězcová reprezentace data vyjádřena v kalendáři, který není aktuálním kalendářem, <xref:System.Globalization.Calendar> třída <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> obsahuje metodu, kterou lze použít společně s <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>metodami, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> pro jednoznačně indikovat datum a období, ke kterému patří. Následující příklad používá <xref:System.Globalization.JapaneseLunisolarCalendar> třídu k poskytnutí obrázku. Nicméně Všimněte si, že pro období ve výsledném řetězci, který obsahuje smysluplný název nebo zkratku namísto celého čísla pro období, vyžaduje <xref:System.Globalization.DateTimeFormatInfo> , abyste vytvořili <xref:System.Globalization.JapaneseCalendar> instanci objektu a vytvořili svůj aktuální kalendář. <xref:System.Globalization.JapaneseLunisolarCalendar> (Kalendář nemůže být aktuálním kalendářem žádné jazykové verze, ale v tomto případě dva kalendáře sdílejí stejné mazání.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

V japonských kalendářích se první rok období posuzování označuje jako Gannen (元年). Například místo Heisei 1 se první rok období Heisei dá popsat jako Heisei Gannen. Rozhraní .NET přijme tuto konvenci v operacích formátování pro data a časy formátované pomocí následujících standardních nebo vlastních formátovacích řetězců data a času, pokud jsou použity <xref:System.Globalization.CultureInfo> s objektem, který představuje jazykovou verzi Japanese-Japonsko ("ja-jp") s <xref:System.Globalization.JapaneseCalendar> třída:

- [Vzor dlouhého data](../base-types/standard-date-and-time-format-strings.md#LongDate), který je označen řetězcem standardního formátu data a času "D".
- [Vzor úplného formátu data a dlouhého času](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), který je označen řetězcem standardního formátu data a času "F".
- [Vzor úplného data krátkého času](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime), který je označen standardním řetězcem formátu data a času "f".
- [Vzor pro rok/měsíc](../base-types/standard-date-and-time-format-strings.md#YearMonth), který je označen řetězcem standardního formátu data a času y nebo y.
- ["GGY" 年 "" nebo "ggy年" [vlastní řetězec formátu data a času](../base-types/custom-date-and-time-format-strings.md).

Například následující příklad zobrazuje datum v prvním roce Heisei období v <xref:System.Globalization.JapaneseCalendar> .

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Pokud je toto chování nežádoucí při formátování operací, můžete obnovit předchozí chování, které vždy představuje první rok v období od "1" místo "Gannen", a to v závislosti na verzi rozhraní .NET:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* můžete přidat následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** Můžete nastavit následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Name | Switch. System. Globalization. FormatJapaneseFirstYearAsANumber |
   |type | REG_SZ |
   |Value | true |

V případě, že je podpora Gannen v případě zakázaných operací formátování, předchozí příklad zobrazí následující výstup:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

Rozhraní .NET bylo také aktualizováno, aby operace analýzy data a času podporovaly řetězce, které obsahují rok reprezentovaný buď 1 nebo Gannen. I když byste to neměli potřebovat, můžete obnovit předchozí chování a rozpoznává pouze "1" jako první rok období. To lze provést následujícím způsobem v závislosti na verzi rozhraní .NET:

- **.NET Core:** Do konfiguračního souboru *. Netcore. Runtime. JSON* můžete přidat následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **.NET Framework 4,6 nebo novější:** Můžete nastavit následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **.NET Framework 4.5.2 nebo novější:** Můžete nastavit následující hodnotu registru:

   |  |  |
   |--|--|  
   |Key | HKEY_LOCAL_MACHINE\Software\Microsoft\.NETFramework\AppContext |
   |Name | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |type | REG_SZ |
   |Value | true | 

## <a name="see-also"></a>Viz také:

- [Postupy: Zobrazení kalendářních dat v jiných než gregoriánského kalendáři](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Vzorku Nástroj pro rozsah týdnů v kalendáři](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Calendar – Třída](xref:System.Globalization.Calendar)
