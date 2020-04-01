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
Typy <xref:System.DateTime> <xref:System.DateTimeOffset> a používají gregoriánský kalendář jako výchozí kalendář. To znamená, že volání `ToString` metody hodnoty data a času zobrazí řetězcovou reprezentaci tohoto data a času v gregoriánském kalendáři, i když toto datum a čas byly vytvořeny pomocí jiného kalendáře. To je znázorněno v následujícím příkladu, který používá dva různé způsoby, jak vytvořit hodnotu data a času s perským <xref:System.DateTime.ToString%2A> kalendářem, ale stále zobrazuje tyto hodnoty data a času v gregoriánském kalendáři při volání metody. Tento příklad odráží dvě běžně používané, ale nesprávné techniky pro zobrazení data v určitém kalendáři.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 K zobrazení data v konkrétním kalendáři lze použít dvě různé techniky. První vyžaduje, aby kalendář byl výchozím kalendářem pro určitou jazykovou verzi. Druhý lze použít s libovolným kalendářem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Zobrazení data výchozího kalendáře jazykové verze  
  
1. Vytvořte instanci objektu kalendáře <xref:System.Globalization.Calendar> odvozeného z třídy, která představuje kalendář, který má být použit.  
  
2. Vytvořte suti, že <xref:System.Globalization.CultureInfo> objekt představuje jazykovou verzi, jejíž formátování bude použito k zobrazení data.  
  
3. Volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody k určení, zda je objekt kalendáře členem <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> pole vrácené vlastností. To znamená, že kalendář může sloužit <xref:System.Globalization.CultureInfo> jako výchozí kalendář pro objekt. Pokud není členem pole, postupujte podle pokynů v části "Chcete-li zobrazit datum v libovolném kalendáři".  
  
4. Přiřaďte objekt <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> kalendáře <xref:System.Globalization.DateTimeFormatInfo> vlastnosti objektu vráceného <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností.  
  
    > [!NOTE]
    > Třída <xref:System.Globalization.CultureInfo> má také <xref:System.Globalization.CultureInfo.Calendar%2A> vlastnost. Je však jen pro čtení a konstantní; nezmění tak, aby odrážel nový výchozí <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> kalendář přiřazený vlastnosti.  
  
5. Volání buď <xref:System.DateTime.ToString%2A> nebo <xref:System.DateTime.ToString%2A> metoda a předat <xref:System.Globalization.CultureInfo> objekt, jehož výchozí kalendář byl změněn v předchozím kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Zobrazení data v libovolném kalendáři  
  
1. Vytvořte instanci objektu kalendáře <xref:System.Globalization.Calendar> odvozeného z třídy, která představuje kalendář, který má být použit.  
  
2. Určete, které prvky data a času by se měly objevit v řetězcové reprezentaci hodnoty data a času.  
  
3. Pro každý prvek data a času, který chcete zobrazit, zavolejte `Get`objektu kalendáře ... Metoda. K dispozici jsou tyto metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>, chcete-li zobrazit rok v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, chcete-li měsíc zobrazit v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, chcete-li zobrazit číslo dne v měsíci v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, chcete-li zobrazit hodinu dne v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, chcete-li zobrazit minuty v hodině v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>, chcete-li zobrazit sekundy v minutě v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, chcete-li zobrazit milisekundy v druhém v příslušném kalendáři.  
  
## <a name="example"></a>Příklad  
 V příkladu se zobrazí datum pomocí dvou různých kalendářů. Zobrazí datum po definování kalendáře hidžra jako výchozí kalendář pro jazykovou verzi ar-JO a zobrazí datum pomocí perského kalendáře, který není podporován jako volitelný kalendář jazykovou verzí fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Každý <xref:System.Globalization.CultureInfo> objekt může podporovat jeden nebo více kalendářů, které jsou označeny vlastností. <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> Jeden z nich je určen jako výchozí kalendář jazykové verze <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> a je vrácena vlastností jen pro čtení. Další z volitelných kalendářů lze označit jako <xref:System.Globalization.Calendar> výchozí přiřazením objektu, který představuje tento kalendář <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnosti vrácené <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastností. Některé kalendáře, například perský kalendář reprezentované <xref:System.Globalization.PersianCalendar> třídou, však neslouží jako volitelné kalendáře pro všechny jazykové verze.  
  
 Příklad definuje opakovaně použitelnou třídu `CalendarUtility`nástrojů kalendáře , která zpracovává mnoho podrobností o generování řetězcové reprezentace data pomocí určitého kalendáře. Třída `CalendarUtility` má následující členy:  
  
- Parametrizovaný konstruktor, jehož <xref:System.Globalization.Calendar> jediný parametr je objekt, ve kterém má být reprezentováno datum. Toto je přiřazeno k soukromému poli třídy.  
  
- `CalendarExists`, soukromá metoda, která vrací logickou hodnotu `CalendarUtility` označující, zda <xref:System.Globalization.CultureInfo> je kalendář reprezentované objektem podporován objektem, který je předán metodě jako parametr. Metoda zalomí volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, ke kterému <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> předá pole.  
  
- `HasSameName`, soukromá metoda <xref:System.Predicate%601> přiřazená delegátovi, která <xref:System.Array.Exists%2A?displayProperty=nameWithType> je předána jako parametr metodě. Každý člen pole je předán metodě, `true`dokud metoda nevrátí . Metoda určuje, zda je název volitelného kalendáře stejný jako `CalendarUtility` kalendář reprezentované objektem.  
  
- `DisplayDate`, přetížená veřejná metoda, která je <xref:System.DateTime> předána dvěma parametry: a nebo <xref:System.DateTimeOffset> hodnota vyjádřená v kalendáři reprezentovaném objektem; `CalendarUtility` a jazykovou verzi, jejíž formátovací pravidla mají být použita. Jeho chování při vrácení řetězcové reprezentace data závisí na tom, zda je cílový kalendář podporován jazykovou verzí, jejíž pravidla formátování mají být použita.  
  
 Bez ohledu na kalendář použitý <xref:System.DateTime> <xref:System.DateTimeOffset> k vytvoření hodnoty nebo v tomto příkladu je tato hodnota obvykle vyjádřena jako gregoriánské datum. Důvodem je, že <xref:System.DateTime> a <xref:System.DateTimeOffset> typy nezachovávají žádné informace kalendáře. Interně jsou reprezentovány jako počet značek, které uplynuly od půlnoci 1. Výklad tohoto čísla závisí na kalendáři. Pro většinu kultur je výchozím kalendářem gregoriánský kalendář.
