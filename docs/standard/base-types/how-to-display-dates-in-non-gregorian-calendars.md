---
title: 'Postupy: Zobrazování dat v jiném než gregoriánském kalendáři'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
ms.openlocfilehash: 8d02b74f63ec5b6260679ae4cea04791681ec238
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523918"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Postupy: Zobrazování dat v jiném než gregoriánském kalendáři
<xref:System.DateTime>Typy a <xref:System.DateTimeOffset> používají gregoriánský kalendář jako výchozí kalendář. To znamená, že volání metody hodnoty data a času `ToString` zobrazuje řetězcové vyjádření data a času v gregoriánském kalendáři, a to i v případě, že se datum a čas vytvořily pomocí jiného kalendáře. To je znázorněno v následujícím příkladu, který používá dva různé způsoby vytvoření hodnoty data a času v Perském kalendáři, ale stále zobrazuje tyto hodnoty data a času v gregoriánském kalendáři při volání <xref:System.DateTime.ToString%2A> metody. Tento příklad odráží dvě běžně používané, ale nesprávné techniky pro zobrazení data v konkrétním kalendáři.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 K zobrazení data v konkrétním kalendáři lze použít dvě různé techniky. První vyžaduje, aby byl kalendář výchozím kalendářem pro konkrétní jazykovou verzi. Druhý lze použít s libovolným kalendářem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Zobrazení data výchozího kalendáře jazykové verze  
  
1. Vytvořte instanci objektu kalendáře odvozenou ze <xref:System.Globalization.Calendar> třídy, která představuje kalendář, který má být použit.  
  
2. Vytvoří instanci <xref:System.Globalization.CultureInfo> objektu představující jazykovou verzi, jejíž formátování se použije k zobrazení data.  
  
3. Zavolejte <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodu pro zjištění, zda je objekt kalendáře členem pole vráceného <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastností. To znamená, že kalendář může sloužit jako výchozí kalendář pro daný <xref:System.Globalization.CultureInfo> objekt. Pokud není členem pole, postupujte podle pokynů v části "zobrazení data v jakémkoli kalendáři".  
  
4. Přiřaďte objekt kalendáře k <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objektu vráceného <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností.  
  
    > [!NOTE]
    > <xref:System.Globalization.CultureInfo>Třída také má <xref:System.Globalization.CultureInfo.Calendar%2A> vlastnost. Je však jen pro čtení a konstanta; nemění se tak, aby odrážela nový výchozí kalendář přiřazený k této <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> Vlastnosti.  
  
5. Zavolejte buď <xref:System.DateTime.ToString%2A> <xref:System.DateTime.ToString%2A> metodu nebo, a předejte ji objektu, <xref:System.Globalization.CultureInfo> jehož výchozí kalendář byl upraven v předchozím kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Zobrazení data v jakémkoli kalendáři  
  
1. Vytvořte instanci objektu kalendáře odvozenou ze <xref:System.Globalization.Calendar> třídy, která představuje kalendář, který má být použit.  
  
2. Určí, které prvky data a času by se měly zobrazit v řetězcové reprezentaci hodnoty data a času.  
  
3. Pro každý prvek data a času, který chcete zobrazit, zavolejte objekt kalendáře `Get` ... Metoda. K dispozici jsou tyto metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, chcete-li zobrazit rok v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, chcete-li zobrazit měsíc v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, chcete-li zobrazit číslo dne v měsíci v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, chcete-li zobrazit hodinu dne v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, chcete-li zobrazit minuty za hodinu v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, chcete-li zobrazit sekundy za minutu v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, chcete-li v příslušném kalendáři zobrazit milisekundy v druhém.  
  
## <a name="example"></a>Příklad  
 V příkladu se zobrazí datum pomocí dvou různých kalendářů. Zobrazuje datum po definování kalendáře hidžra jako výchozího kalendáře pro jazykovou verzi ar-JO a zobrazuje datum pomocí perského kalendáře, který není podporován jako volitelný kalendář pomocí jazykové verze FA-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Každý <xref:System.Globalization.CultureInfo> objekt může podporovat jeden nebo více kalendářů, které jsou označeny <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> vlastností. Jedna z nich je určena jako výchozí kalendář jazykové verze a je vrácena vlastností jen pro čtení <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> . Další z volitelných kalendářů lze označit jako výchozí přiřazením <xref:System.Globalization.Calendar> objektu, který představuje tento kalendář, na <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost vrácenou <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností. Některé kalendáře, jako je například perské kalendář reprezentovaný <xref:System.Globalization.PersianCalendar> třídou, ale neslouží jako volitelné kalendáře pro jakoukoli jazykovou verzi.  
  
 Příklad definuje opakovaně použitelnou třídu nástrojů kalendáře, `CalendarUtility` aby zpracovávala mnoho podrobností o generování řetězcové reprezentace data pomocí konkrétního kalendáře. `CalendarUtility`Třída má následující členy:  
  
- Parametrizovaný konstruktor, jehož jeden parametr je <xref:System.Globalization.Calendar> objekt, ve kterém má být reprezentované datum. Toto je přiřazeno k soukromému poli třídy.  
  
- `CalendarExists`, soukromá metoda, která vrací logickou hodnotu, která označuje, zda je kalendář reprezentovaný `CalendarUtility` objektem podporován <xref:System.Globalization.CultureInfo> objektem, který je předán metodě jako parametr. Metoda zabalí volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, na kterou předává <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> pole.  
  
- `HasSameName`, soukromá metoda přiřazená k <xref:System.Predicate%601> delegátovi, který je předán jako parametr <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodě. Každý člen pole je předán metodě, dokud metoda nevrátí `true` . Metoda určuje, zda je název volitelného kalendáře stejný jako kalendář reprezentovaný `CalendarUtility` objektem.  
  
- `DisplayDate`, přetížená veřejná metoda, která je předána dvěma parametrům: <xref:System.DateTime> hodnotu nebo <xref:System.DateTimeOffset> pro vyjádření do kalendáře reprezentovaného `CalendarUtility` objektem a jazykové verzi, jejíž pravidla formátování má být použita. Chování při vrácení řetězcové reprezentace data závisí na tom, zda je cílový kalendář podporován jazykovou verzí, jejíž pravidla formátování mají být použita.  
  
 Bez ohledu na kalendář použitý k vytvoření <xref:System.DateTime> <xref:System.DateTimeOffset> hodnoty nebo v tomto příkladu je tato hodnota obvykle vyjádřena jako gregoriánské datum. Důvodem je, že <xref:System.DateTime> <xref:System.DateTimeOffset> typy a neuchovávají žádné informace v kalendáři. Interně jsou reprezentovány jako počet taktů, které uplynuly od půlnoci 1. ledna 0001. Výklad tohoto čísla závisí na kalendáři. Pro většinu kultur je výchozím kalendářem gregoriánský kalendář.
