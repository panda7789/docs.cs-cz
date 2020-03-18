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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400587"
---
# <a name="work-with-calendars"></a>Práce s kalendáři

Ačkoli hodnoty data a času představují konkrétní časový okamžik, je řetězcové vyjádření závislé na jazykové verzi a závisí jak na konvencích použitých k zobrazení hodnoty data a času podle konkrétní jazykové verze, tak na kalendáři používaném danou jazykovou verzí. Toto téma zkoumá podporu pro kalendáře v rozhraní .NET a popisuje použití tříd kalendáře při práci s hodnotami kalendářních dat.

## <a name="calendars-in-net"></a>Kalendáře v rozhraní .NET

Všechny kalendáře v rozhraní .NET jsou odvozeny <xref:System.Globalization.Calendar?displayProperty=nameWithType> z třídy, která poskytuje základní implementaci kalendáře. Jedna z tříd, která <xref:System.Globalization.Calendar> dědí <xref:System.Globalization.EastAsianLunisolarCalendar> z třídy je třída, což je základní třída pro všechny lunisolar kalendáře. Rozhraní .NET obsahuje následující implementace kalendáře:

- <xref:System.Globalization.ChineseLunisolarCalendar>, který představuje čínský lunisolar kalendář.

- <xref:System.Globalization.GregorianCalendar>, který představuje gregoriánský kalendář. Tento kalendář je dále rozdělen na podtypy (například arabština a <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> francouzština na Středním východě), které jsou definovány výčtem. Vlastnost <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> určuje podtyp gregoriánského kalendáře.

- <xref:System.Globalization.HebrewCalendar>, který představuje hebrejský kalendář.

- <xref:System.Globalization.HijriCalendar>, který představuje kalendář hidžra.

- <xref:System.Globalization.JapaneseCalendar>, který představuje japonský kalendář.

- <xref:System.Globalization.JapaneseLunisolarCalendar>, který představuje japonský lunisolar kalendář.

- <xref:System.Globalization.JulianCalendar>, který představuje juliánský kalendář.

- <xref:System.Globalization.KoreanCalendar>, který představuje korejský kalendář.

- <xref:System.Globalization.KoreanLunisolarCalendar>, který představuje korejský lunisolar kalendář.

- <xref:System.Globalization.PersianCalendar>, který představuje perský kalendář.

- <xref:System.Globalization.TaiwanCalendar>, který představuje tchajwanský kalendář.

- <xref:System.Globalization.TaiwanLunisolarCalendar>, který představuje tchajwanský lunisolar kalendář.

- <xref:System.Globalization.ThaiBuddhistCalendar>, který představuje thajský buddhistický kalendář.

- <xref:System.Globalization.UmAlQuraCalendar>, který představuje kalendář Um Al Qura.

Kalendář lze použít jedním ze dvou způsobů:

- Jako kalendář, který používá konkrétní jazyková verze. Každý <xref:System.Globalization.CultureInfo> objekt má aktuální kalendář, což je kalendář, který objekt aktuálně používá. Řetězcové vyjádření hodnot data a času automaticky odrážejí aktuální jazykovou verzi a aktuální kalendář. Aktuálním kalendářem je obvykle výchozí kalendář dané jazykové verze. <xref:System.Globalization.CultureInfo>objekty mají také volitelné kalendáře, které obsahují další kalendáře, které může jazyková verze použít.

- Jako samostatný kalendář, který není závislý na konkrétní jazykové verzi. V tomto <xref:System.Globalization.Calendar> případě metody se používají k vyjádření data jako hodnoty, které odrážejí kalendář.

Všimněte si, <xref:System.Globalization.ChineseLunisolarCalendar>že <xref:System.Globalization.JapaneseLunisolarCalendar> <xref:System.Globalization.JulianCalendar>šest <xref:System.Globalization.KoreanLunisolarCalendar> <xref:System.Globalization.PersianCalendar>tříd <xref:System.Globalization.TaiwanLunisolarCalendar> kalendáře – , , , , a – lze použít pouze jako samostatné kalendáře. Tyto kalendáře nepoužívá žádná jazyková verze jako výchozí kalendář nebo jako volitelný kalendář.

## <a name="calendars-and-cultures"></a>Kalendáře a kultury

Každá jazyková verze má výchozí kalendář, který je definován vlastností. <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> Vlastnost <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vrátí pole <xref:System.Globalization.Calendar> objektů, které určuje všechny kalendáře podporované konkrétní jazykovou verzi, včetně výchozího kalendáře této jazykové verze.

Následující příklad ilustruje <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnosti a. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> Vytvoří `CultureInfo` objekty pro thajské (Thajsko) a japonské (Japonsko) jazykové verze a zobrazí jejich výchozí a volitelné kalendáře. Všimněte si, že v obou případech je do <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> kolekce zahrnut také výchozí kalendář jazykové verze.

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

Kalendář aktuálně používán určitým <xref:System.Globalization.CultureInfo> objektem je definován <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastností jazykové verze. <xref:System.Globalization.DateTimeFormatInfo> Objekt jazykové verze je vrácena vlastností. <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Při vytvoření jazykové verze je jeho výchozí hodnota stejná jako hodnota vlastnosti. <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> Aktuální kalendář jazykové verze však můžete změnit na libovolný kalendář obsažený <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> v poli vráceném vlastností. Pokud se pokusíte nastavit aktuální kalendář na kalendář, <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> který není <xref:System.ArgumentException> součástí hodnoty vlastnosti, je vyvolána.

Následující příklad znázorňuje změnu kalendáře používaného jazykovou verzí Arabština (Saúdská Arábie). Nejprve konkretizovat hodnotu <xref:System.DateTime> a zobrazí ji pomocí aktuální jazykové verze - což je v tomto případě angličtina (Spojené státy) - a aktuální jazykovou verzi kalendáře (což je v tomto případě gregoriánský kalendář). Poté změní aktuální jazykovou verzi na verzi Arabština (Saúdská Arábie) a zobrazí datum pomocí výchozího kalendáře Um-al-Qura. Potom volá `CalendarExists` metodu k určení, zda kalendář hidžra je podporován a arabština (Saúdská Arábie) jazykové verze. Vzhledem k tomu, že kalendář je podporován, změní aktuální kalendář na kalendář Hidžra a znovu zobrazí datum. V obou případech je datum zobrazeno pomocí aktuálního kalendáře aktuální jazykové verze.

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>Data a kalendáře

S výjimkou konstruktory, které obsahují parametr <xref:System.Globalization.Calendar> typu a povolit prvky data (to znamená, měsíc, den a rok) tak, <xref:System.DateTimeOffset> aby odrážely hodnoty v určeném kalendáři, a <xref:System.DateTime> hodnoty jsou vždy založeny na gregoriánském kalendáři. To například znamená, <xref:System.DateTime.Year%2A?displayProperty=nameWithType> že vlastnost vrátí rok v gregoriánském kalendáři a <xref:System.DateTime.Day%2A?displayProperty=nameWithType> vlastnost vrátí den v měsíci v gregoriánském kalendáři.

> [!IMPORTANT]
> Je důležité mít na paměti, že existuje rozdíl mezi hodnotou data a řetězcovým vyjádřením tohoto data. První zmíněná položka je založena na gregoriánském kalendáři, druhá zmíněná položka pak vychází z aktuálního kalendáře konkrétní jazykové verze.

Následující příklad ilustruje tento <xref:System.DateTime> rozdíl mezi <xref:System.Globalization.Calendar> vlastnostmi a jejich odpovídající metody. V tomto příkladu je aktuální jazykovou verzí Arabština (Egypt) a aktuální kalendář je Um-al-Qura. Hodnota <xref:System.DateTime> je nastavena na patnáctý den sedmého měsíce roku 2011. Je zřejmé, že je interpretován jako gregoriánské datum, protože tyto <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> stejné hodnoty jsou vráceny metodou při použití konvencí invariantní jazykové verze. Řetězcové vyjádření data, které je naformátováno pomocí konvencí aktuální jazykové verze, je 14/08/32, což odpovídá datu v kalendáři Um-al-Qura. Dále členové `DateTime` a `Calendar` jsou používány k vrácení den, měsíc <xref:System.DateTime> a rok hodnoty. V každém případě hodnoty <xref:System.DateTime> vrácené členy odrážejí hodnoty v gregoriánském <xref:System.Globalization.UmAlQuraCalendar> kalendáři, zatímco hodnoty vrácené členy odrážejí hodnoty v kalendáři Uum al-Qura.

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiate-dates-based-on-a-calendar"></a>Vytváření instanci dat na základě kalendáře

Vzhledem k tomu, <xref:System.DateTime> že a <xref:System.DateTimeOffset> hodnoty jsou založeny na gregoriánském <xref:System.Globalization.Calendar> kalendáři, musíte volat přetížený konstruktor, který obsahuje parametr typu k vytvoření instance hodnoty data, pokud chcete použít hodnoty den, měsíc nebo rok z jiného kalendáře. Můžete také volat jeden z přetížení metody konkrétního kalendáře <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> k vytvoření <xref:System.DateTime> instance objektu na základě hodnot konkrétního kalendáře.

Následující příklad inkonvaluje <xref:System.DateTime> jednu hodnotu předáním objektu <xref:System.Globalization.HebrewCalendar> konstruktoru <xref:System.DateTime> a vytvoří druhou <xref:System.DateTime> hodnotu voláním <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> metody. Vzhledem k tomu, že dvě hodnoty jsou vytvořeny s <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> identické hodnoty <xref:System.DateTime> z hebrejského kalendáře, volání metody ukazuje, že dvě hodnoty jsou stejné.

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="represent-dates-in-the-current-calendar"></a>Představují data v aktuálním kalendáři

Metoda formátování data a času používá při konverzi dat do řetězců vždy aktuální kalendář. To znamená, že řetězcové vyjádření roku, měsíce a dne v měsíci odpovídá aktuálnímu kalendáři a nemusí nutně zohledňovat gregoriánský kalendář.

Následující příklad znázorňuje vliv aktuálního kalendáře na řetězcové vyjádření data. Nastaví aktuální jazykovou verzi Čínština (tradiční, Tchaj-wan) a vytvoří instanci hodnoty data. Potom zobrazí aktuální kalendář a datum, změní <xref:System.Globalization.TaiwanCalendar>aktuální kalendář na , a zobrazí aktuální kalendář a datum znovu. Při prvním zobrazení je datum vyjádřeno jako datum v gregoriánském kalendáři. Při druhém zobrazení je datum vyjádřeno jako datum v tchajwanském kalendáři.

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="represent-dates-in-a-non-current-calendar"></a>Představují data v neaktuálním kalendáři

Chcete-li reprezentovat datum pomocí kalendáře, který není aktuální kalendář určité jazykové <xref:System.Globalization.Calendar> verze, musíte volat metody tohoto objektu. Například <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>, <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody převést rok, měsíc a den na hodnoty, které odrážejí konkrétní kalendář.

> [!WARNING]
> Vzhledem k tomu, že některé kalendáře neobsahují volitelné kalendáře žádné jazykové verze, vyžaduje zobrazení dat v těchto kalendářích vždy volání metod kalendáře. To platí pro všechny kalendáře, <xref:System.Globalization.EastAsianLunisolarCalendar>které <xref:System.Globalization.JulianCalendar>jsou <xref:System.Globalization.PersianCalendar> odvozeny z , , a třídy.

Následující příklad používá <xref:System.Globalization.JulianCalendar> objekt k vytvoření instance data, 9. Pokud je toto datum zobrazeno pomocí výchozího (gregoriánského) kalendáře, má podobu 22. ledna 1905. Volání jednotlivých <xref:System.Globalization.JulianCalendar> metod umožňují, aby bylo datum reprezentováno v juliánském kalendáři.

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>Kalendáře a rozsahy dat

Nejbližší datum podporované kalendářem je označeno <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> vlastností tohoto kalendáře. Pro <xref:System.Globalization.GregorianCalendar> třídu je toto datum 1.1.0001 CE Většina ostatních kalendářů v rozhraní .NET podporuje pozdější datum. Pokus o práci s hodnotou data a času, která předchází nejbližšímu podporovanému datu kalendáře, vyvolá výjimku. <xref:System.ArgumentOutOfRangeException>

Existuje však jedna důležitá výjimka. Výchozí (neinicializovaná) <xref:System.DateTime> hodnota <xref:System.DateTimeOffset> objektu a <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> objektu se rovná hodnotě. Pokud se pokusíte naformátovat toto datum v kalendáři, který nepodporuje 1.ledna 0001 CE a neposkytujete specifikátor formátu, metoda formátování používá specifikátor formátu "s" (seřaditelný vzor data a času) namísto specifikátoru formátu "G" (obecný vzorec data a času). V důsledku toho operace formátování nevyvolá <xref:System.ArgumentOutOfRangeException> výjimku. Namísto toho vrátí nepodporované datum. To je znázorněno v následujícím příkladu, <xref:System.DateTime.MinValue?displayProperty=nameWithType> který zobrazuje hodnotu, když je aktuální jazyková verze nastavena na japonštinu (Japonsko) s japonským kalendářem a na arabštinu (Egypt) s kalendářem Um Al Qura. Také nastaví aktuální jazykovou verzi angličtiny <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> (Spojené státy) <xref:System.Globalization.CultureInfo> a volá metodu s každým z těchto objektů. V obou případech je datum zobrazeno pomocí seřaditelného vzorce data/času.

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="work-with-eras"></a>Práce s epochami

Data v kalendářích jsou obvykle rozdělena do období. <xref:System.Globalization.Calendar> Třídy v rozhraní .NET však nepodporují každou éru definovanou kalendářem a většina <xref:System.Globalization.Calendar> tříd podporuje pouze jednu éru. Pouze <xref:System.Globalization.JapaneseCalendar> třídy a <xref:System.Globalization.JapaneseLunisolarCalendar> podporují více epoch.

> [!IMPORTANT]
> Éra Reiwa, nová éra <xref:System.Globalization.JapaneseCalendar> v <xref:System.Globalization.JapaneseLunisolarCalendar>a , začíná v květnu 1, 2019. Tato změna ovlivní všechny aplikace, které používají tyto kalendáře. Další informace naleznete v následujících článcích:
>
> - [Zpracování nové éry v japonském kalendáři v rozhraní .NET](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/), které dokumentuje funkce přidané do rozhraní .NET pro podporu kalendářů s více obdobími a popisuje osvědčené postupy, které se mají používat při zpracování kalendářů s více obdobími.
> - [Připravte aplikaci na změnu japonské éry](/windows/uwp/design/globalizing/japanese-era-change), která poskytuje informace o testování aplikací v systému Windows, abyste zajistili jejich připravenost na změnu éry.
> - [Souhrn nových aktualizací japonské éry pro rozhraní .NET Framework](https://support.microsoft.com/help/4477957/new-japanese-era-updates-for-net-framework), který obsahuje aktualizace rozhraní .NET Framework pro jednotlivé verze systému Windows související s novou japonskou kalendářní érou, bere na vědomí nové funkce rozhraní .NET Framework pro podporu více e-mailů a obsahuje položky, které je třeba hledat při testování aplikací.

Éra ve většině kalendářů označuje extrémně dlouhé časové období. Například v gregoriánském kalendáři se aktuální doba rozprostírá více než dvě tisíciletí. Pro <xref:System.Globalization.JapaneseCalendar> a <xref:System.Globalization.JapaneseLunisolarCalendar>, dva kalendáře, které podporují více epoch, to není tento případ. Éra odpovídá období císařovy vlády. Podpora více epoch, zejména pokud není známa horní hranice současné éry, představuje zvláštní výzvy.

### <a name="eras-and-era-names"></a>Názvy epoch a ér

V rozhraní .NET jsou celá čísla, která představují éry podporované konkrétní implementací kalendáře, uložena v <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> poli v opačném pořadí. Aktuální období (což je éra s nejnovějším časovým rozsahem) je na indexu nula a pro <xref:System.Globalization.Calendar> třídy, které podporují více období, každý po sobě jdoucí index odráží předchozí období. Statická <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> vlastnost definuje index aktuálního období <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> v poli; je konstanta, jejíž hodnota je vždy nula. Jednotlivé <xref:System.Globalization.Calendar> třídy také obsahují statická pole, která vracejí hodnotu aktuálního období. Jsou uvedeny v následující tabulce.

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

Název, který odpovídá určitému číslu éry, lze načíst <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> předáním čísla éry metodě nebo. <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> Následující příklad volá tyto metody k načtení <xref:System.Globalization.GregorianCalendar> informací o podpoře éry ve třídě. Zobrazí gregoriánský kalendářní datum, které odpovídá 1.ledna druhého roku aktuálního roku, stejně jako gregoriánské kalendářní datum, které odpovídá 1.ledna druhého roku každého podporovaného japonského kalendářního období.

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

Kromě toho řetězec „o“ vlastního formátu data a času obsahuje název období kalendáře v řetězcovém vyjádření data a času. Další informace naleznete [v tématu Vlastní formátovací řetězce data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).

### <a name="instantiatie-a-date-with-an-era"></a>Instantiatie datum s érou

Pro dvě <xref:System.Globalization.Calendar> třídy, které podporují více období, může být nejednoznačné datum, které se skládá z určitého roku, měsíce a dne v měsíci. Například všechny epochy <xref:System.Globalization.JapaneseCalendar> podporované have years, jehož číslo je 1. Pokud není období stanoveno, pak metody data a času a kalendáře obvykle předpokládají, že hodnoty patří do aktuálního období. To platí pro <xref:System.DateTime.%23ctor%2A> <xref:System.DateTimeOffset.%23ctor%2A> konstruktory a, které <xref:System.Globalization.Calendar>obsahují parametry typu , stejně jako [metody JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) a [JapaneseLunisolarCalendar.ToDateTime.](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)) Následující příklad vytvoří instance data, které představuje 1. Pokud provedete příklad, když éra Reiwa je aktuální éra, datum je interpretováno jako druhý rok éry Reiwa. Éra, 啦中, předchází rok v řetězci vrácené <xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType> metodou a odpovídá 1.ledna 2020, v gregoriánském kalendáři. (Éra Reiwy začíná v roce 2019 gregoriánského kalendáře.)

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

Pokud se však změní období, záměr tohoto kódu se stane nejednoznačným. Je datum, které má představovat druhý rok současné hodu, nebo má představovat druhý rok éry Heisei? Existují dva způsoby, jak se této nejednoznačnosti vyhnout:

- Vytvořte instanci hodnoty data a <xref:System.Globalization.GregorianCalendar> času pomocí výchozí třídy. Potom můžete použít japonský kalendář nebo japonský lunisolar kalendář pro řetězcovou reprezentaci kalendářních dat, jak ukazuje následující příklad.

  [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
  [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- Volání metody data a času, která explicitně určuje období. To zahrnuje následující metody:

  - Metoda <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> <xref:System.Globalization.JapaneseCalendar> nebo <xref:System.Globalization.JapaneseLunisolarCalendar> třídy.

  - A <xref:System.DateTime> <xref:System.DateTimeOffset> nebo parsing metoda, <xref:System.DateTime.TryParse%2A> <xref:System.DateTime.ParseExact%2A>například <xref:System.DateTime.TryParseExact%2A> <xref:System.Globalization.DateTimeStyles> <xref:System.DateTime.Parse%2A>, , nebo , který obsahuje řetězec, který má být analyzována a volitelně argument, pokud aktuální jazyková verze je japonsko-Japonsko ("ja-JP") a kalendář této jazykové verze je <xref:System.Globalization.JapaneseCalendar>. Řetězec, který má být analyzován, musí obsahovat éru.

  - A <xref:System.DateTime> <xref:System.DateTimeOffset> nebo analýza metoda, `provider` která obsahuje <xref:System.IFormatProvider>parametr typu . `provider`musí být <xref:System.Globalization.CultureInfo> objekt, který představuje jazykovou verzi Japan-Japan ("ja-JP"), jejíž aktuální kalendář je, <xref:System.Globalization.JapaneseCalendar> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, jehož <xref:System.Globalization.DateTimeFormatInfo.Calendar> vlastnost je <xref:System.Globalization.JapaneseCalendar>. Řetězec, který má být analyzován, musí obsahovat éru.

  Následující příklad používá tři z těchto metod k vytvoření instance data a času v éře Meiji, která začala 8.

  [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
  [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> Při práci s kalendáři, které podporují více období, *vždy* použijte gregoriánské datum k vytvoření instance data nebo určete éru při vytváření instancí data a času na základě tohoto kalendáře.

Při zadávání éry <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)> metody zadejte index era ve <xref:System.Globalization.Calendar.Eras> vlastnosti kalendáře. Pro kalendáře, jejichž epochy se mohou změnit, však tyto indexy nejsou konstantní hodnoty; aktuální éra je na indexu 0 a nejstarší `Eras.Length - 1`éra je na indexu . Při přidání nové éry do kalendáře se indexy předchozích období zvýší o jednu. Můžete zadat odpovídající index éry takto:

- Pro data v aktuálním období vždy <xref:System.Globalization.Calendar.CurrentEra> použijte vlastnost kalendáře.

- Pro data v zadaném <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> období použijte metodu k načtení indexu, který odpovídá zadanému názvu éry. To vyžaduje, <xref:System.Globalization.JapaneseCalendar> aby byl aktuální <xref:System.Globalization.CultureInfo> kalendář objektu, který představuje ja-JP jazykovou verzi.  (Tato technika funguje <xref:System.Globalization.JapaneseLunisolarCalendar> také, protože podporuje stejné epochy <xref:System.Globalization.JapaneseCalendar>jako .) Předchozí příklad ilustruje tento přístup.

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>Kalendáře, epochy a rozsahy dat: Uvolněné kontroly rozsahu

Velmi podobně jako jednotlivé kalendáře mají podporované rozsahy <xref:System.Globalization.JapaneseCalendar> <xref:System.Globalization.JapaneseLunisolarCalendar> dat, epochy v a třídy mají také podporované rozsahy. Dříve rozhraní .NET používalo přísné kontroly rozsahu období, aby bylo zajištěno, že datum určité období bylo v rozsahu tohoto období. To znamená, že pokud je datum mimo rozsah zadaného období, metoda vyvolá . <xref:System.ArgumentOutOfRangeException> V současné době rozhraní .NET ve výchozím nastavení používá uvolněnou kontrolu rozsahu. Aktualizace všech verzí rozhraní .NET zavedly kontroly rozsahu uvolněné éry. pokus o vytvoření instance data specifického pro éru, který je mimo rozsah zadaného období "přetečení" do následujícího období a není vyvolána žádná výjimka.

Následující příklad se pokouší vytvořit konkretizovat datum v 65. Toto datum odpovídá <xref:System.Globalization.JapaneseCalendar>9.ledna 1990, což je mimo rozsah éry Showa v . Jak ukazuje výstup z příkladu, datum zobrazené v příkladu je 9.

  [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
  [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

Pokud jsou uvolněné kontroly rozsahu nežádoucí, můžete obnovit přísné kontroly rozsahu několika způsoby v závislosti na verzi rozhraní .NET, na které je aplikace spuštěna:

- **Jádro .NET:** Do konfiguračního souboru *.netcore.runtime.json* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
    }
  }
  ```

- **Rozhraní .NET Framework 4.6 nebo novější:** V souboru *app.config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
    </runtime>
  </configuration>
  ```

- **Rozhraní .NET Framework 4.5.2 nebo starší:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Klíč** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\Kontext aplikace** |
   | **Název** | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   | **Typ** | REG_SZ |
   | **Hodnotu** | true |

S povolenou přísnou kontrolou rozsahu, <xref:System.ArgumentOutOfRangeException> v předchozím příkladu vyvolá a zobrazí následující výstup:

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="represent-dates-in-calendars-with-multiple-eras"></a>Představují data v kalendářích s více epochami

Pokud <xref:System.Globalization.Calendar> objekt podporuje období a je aktuální <xref:System.Globalization.CultureInfo> kalendář objektu, je éra zahrnuta do řetězcové reprezentace hodnoty data a času pro úplné datum a čas, dlouhé datum a krátké vzory data. Následující příklad zobrazuje tyto vzorce dat, kdy je nastavena aktuální jazyková verze Japonština (Japonsko) a aktuálním kalendářem je japonský kalendář.

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> Třída <xref:System.Globalization.JapaneseCalendar> je jedinou třídou kalendáře v rozhraní .NET, která podporuje data ve <xref:System.Globalization.CultureInfo> více než jednom <xref:System.Globalization.CultureInfo> období a která může být aktuálním kalendářem objektu - konkrétně objektu, který představuje japonskou jazykovou verzi.

Specifikátor vlastního formátu „o“ zahrnuje období ve výsledném řetězci všech kalendářů. Následující příklad používá vlastní řetězec formátu „MM-dd-rrrr g“ pro vyjádření období ve výsledném řetězci, pokud je aktuální kalendář nastaven na gregoriánský kalendář.

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

V <xref:System.Globalization.Calendar> <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType> <xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>případech, kdy je řetězcová reprezentace data vyjádřena v kalendáři, který není aktuálním kalendářem, třída obsahuje metodu, kterou lze použít společně s , <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType>a <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> metody k jednoznačnému označení data a období, ke kterému patří. Následující příklad používá <xref:System.Globalization.JapaneseLunisolarCalendar> třídu k poskytnutí ilustrace. Mějte však na paměti, že zahrnutí smysluplného názvu nebo zkratky namísto celého čísla pro <xref:System.Globalization.DateTimeFormatInfo> období ve <xref:System.Globalization.JapaneseCalendar> výsledném řetězci vyžaduje vytvoření instance objektu a vytvoření jeho aktuálního kalendáře. (Kalendář <xref:System.Globalization.JapaneseLunisolarCalendar> nemůže být aktuální kalendář žádné jazykové verze, ale v tomto případě dva kalendáře sdílejí stejné epochy.)

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

V japonských kalendářích se první rok éry nazývá Gannen .) Například místo Heisei 1 lze první rok éry Heisei popsat jako Heisei Gannen. Rozhraní .NET přijímá tuto konvenci v operacích formátování pro data a časy formátované následujícími <xref:System.Globalization.CultureInfo> standardními nebo vlastními řetězci formátu data a <xref:System.Globalization.JapaneseCalendar> času, pokud jsou použity s objektem, který představuje jazykovou verzi Japonsko -Japonsko ("ja-JP") se třídou:

- [Vzor dlouhého data](../base-types/standard-date-and-time-format-strings.md#LongDate)označený standardním formátovacím řetězcem "D" data a času.
- [Úplný vzor dlouhého času](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime), označený standardním formátovacím řetězcem "F" data a času.
- [Úplný časový vzor s datem](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)označený standardním formátovacím řetězcem "f" data a času.
- [Vzor rok/měsíc](../base-types/standard-date-and-time-format-strings.md#YearMonth)označený standardním formátovacím řetězcem y nebo "y" data a času.
- [Vlastní formát ovací [řetězec data a času](../base-types/custom-date-and-time-format-strings.md)"ggy'"nebo "ggy".

Například následující příklad zobrazuje datum v prvním roce éry Heisei v . <xref:System.Globalization.JapaneseCalendar>

  [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
  [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

Pokud toto chování je nežádoucí ve formátování operací, můžete obnovit předchozí chování, které vždy představuje první rok éry jako "1" spíše než "Gannen", postupujte takto, v závislosti na verzi .NET:

- **Jádro .NET:** Do konfiguračního souboru *.netcore.runtime.json* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
    }
  }
  ```

- **Rozhraní .NET Framework 4.6 nebo novější:** V souboru *app.config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
    </runtime>
  </configuration>
  ```

- **Rozhraní .NET Framework 4.5.2 nebo starší:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Klíč** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\Kontext aplikace** |
   | **Název** | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   | **Typ** | REG_SZ |
   | **Hodnotu** | true |

Při zakázání podpory gannenu při operacích formátování se v předchozím příkladu zobrazí následující výstup:

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

Rozhraní .NET byla také aktualizována tak, aby operace analýzy dat a času podporovaly řetězce podpory, které obsahují rok reprezentované jako "1" nebo Gannen. I když byste to neměli dělat, můžete obnovit předchozí chování rozpozná pouze "1" jako první rok éry. V závislosti na verzi rozhraní .NET to lze provést následujícím způsobem:

- **Jádro .NET:** Do konfiguračního souboru *.netcore.runtime.json* přidejte následující:

  ```json
  "runtimeOptions": {
    "configProperties": {
        "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
    }
  }
  ```

- **Rozhraní .NET Framework 4.6 nebo novější:** V souboru *app.config* nastavte následující přepínač AppContext:

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
    </runtime>
  </configuration>
  ```

- **Rozhraní .NET Framework 4.5.2 nebo starší:** Nastavte následující hodnotu registru:

   |  |  |
   |--|--|
   | **Klíč** | **HKEY_LOCAL_MACHINE\Software\Microsoft\\. NETFramework\Kontext aplikace** |
   | **Název** | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   | **Typ** | REG_SZ |
   | **Hodnotu** | true |

## <a name="see-also"></a>Viz také

- [Postup: Zobrazení kalendářních dat v negregoriánských kalendářích](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [Ukázka: Nástroj rozsah kalendářního týdne](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [Třída kalendáře](xref:System.Globalization.Calendar)
