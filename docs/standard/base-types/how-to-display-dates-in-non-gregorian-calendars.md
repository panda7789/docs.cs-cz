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
ms.openlocfilehash: 455996d091f92367667e7077a4524898cd8face6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138757"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Postupy: Zobrazování dat v jiném než gregoriánském kalendáři
Typy <xref:System.DateTime> a <xref:System.DateTimeOffset> používají gregoriánský kalendář jako výchozí kalendář. To znamená, že volání hodnoty data a času `ToString` Metoda zobrazuje řetězcové vyjádření data a času v gregoriánském kalendáři, i když bylo toto datum a čas Vytvořeno pomocí jiného kalendáře. To je znázorněno v následujícím příkladu, který používá dva různé způsoby vytvoření hodnoty data a času v Perském kalendáři, ale stále zobrazuje tyto hodnoty data a času v gregoriánském kalendáři při volání metody <xref:System.DateTime.ToString%2A>. Tento příklad odráží dvě běžně používané, ale nesprávné techniky pro zobrazení data v konkrétním kalendáři.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 K zobrazení data v konkrétním kalendáři lze použít dvě různé techniky. První vyžaduje, aby byl kalendář výchozím kalendářem pro konkrétní jazykovou verzi. Druhý lze použít s libovolným kalendářem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Zobrazení data výchozího kalendáře jazykové verze  
  
1. Vytvořte instanci objektu kalendáře odvozeného od <xref:System.Globalization.Calendar> třídy, která představuje kalendář, který má být použit.  
  
2. Vytvoří instanci objektu <xref:System.Globalization.CultureInfo> reprezentující jazykovou verzi, jejíž formátování se použije k zobrazení data.  
  
3. Voláním metody <xref:System.Array.Exists%2A?displayProperty=nameWithType> určíte, zda je objekt kalendáře členem pole vráceného vlastností <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>. To znamená, že kalendář může sloužit jako výchozí kalendář pro objekt <xref:System.Globalization.CultureInfo>. Pokud není členem pole, postupujte podle pokynů v části "zobrazení data v jakémkoli kalendáři".  
  
4. Přiřaďte objekt Calendar k vlastnosti <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> objektu <xref:System.Globalization.DateTimeFormatInfo> vráceného vlastností <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>.  
  
    > [!NOTE]
    > Třída <xref:System.Globalization.CultureInfo> má také vlastnost <xref:System.Globalization.CultureInfo.Calendar%2A>. Je však jen pro čtení a konstanta; nemění se tak, aby odrážela nový výchozí kalendář přiřazený k vlastnosti <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType>.  
  
5. Zavolejte buď metodu <xref:System.DateTime.ToString%2A>, nebo metodu <xref:System.DateTime.ToString%2A> a předejte jí objekt <xref:System.Globalization.CultureInfo>, jehož výchozí kalendář byl upraven v předchozím kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Zobrazení data v jakémkoli kalendáři  
  
1. Vytvořte instanci objektu kalendáře odvozeného od <xref:System.Globalization.Calendar> třídy, která představuje kalendář, který má být použit.  
  
2. Určí, které prvky data a času by se měly zobrazit v řetězcové reprezentaci hodnoty data a času.  
  
3. Pro každý prvek data a času, který chcete zobrazit, zavolejte `Get`objektu kalendáře... Metoda. K dispozici jsou následující metody:  
  
    - <xref:System.Globalization.Calendar.GetYear%2A>pro zobrazení roku v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMonth%2A>, chcete-li zobrazit měsíc v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetDayOfMonth%2A>pro zobrazení čísla dne v měsíci v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetHour%2A>, chcete-li zobrazit hodinu dne v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMinute%2A>, chcete-li zobrazit minuty za hodinu v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetSecond%2A>pro zobrazení sekund za minutu v příslušném kalendáři.  
  
    - <xref:System.Globalization.Calendar.GetMilliseconds%2A>, chcete-li v příslušném kalendáři zobrazit milisekundy v druhém.  
  
## <a name="example"></a>Příklad  
 V příkladu se zobrazí datum pomocí dvou různých kalendářů. Zobrazuje datum po definování kalendáře hidžra jako výchozího kalendáře pro jazykovou verzi ar-JO a zobrazuje datum pomocí perského kalendáře, který není podporován jako volitelný kalendář pomocí jazykové verze FA-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Každý objekt <xref:System.Globalization.CultureInfo> může podporovat jeden nebo více kalendářů, které jsou označeny vlastností <xref:System.Globalization.CultureInfo.OptionalCalendars%2A>. Jedna z nich je určena jako výchozí kalendář jazykové verze a je vrácena vlastností <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> pouze pro čtení. Další z volitelných kalendářů lze označit jako výchozí přiřazením objektu <xref:System.Globalization.Calendar>, který představuje tento kalendář, do vlastnosti <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vrácené vlastností <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Některé kalendáře, jako je například příklad perského kalendáře reprezentovaného třídou <xref:System.Globalization.PersianCalendar>, neslouží jako volitelné kalendáře pro žádnou jazykovou verzi.  
  
 Příklad definuje opakovaně použitelnou třídu nástrojů kalendáře `CalendarUtility`, aby zpracovávala mnoho podrobností o generování řetězcové reprezentace data pomocí konkrétního kalendáře. Třída `CalendarUtility` má následující členy:  
  
- Parametrizovaný konstruktor, jehož jedním parametrem je <xref:System.Globalization.Calendar> objekt, ve kterém má být reprezentované datum. Toto je přiřazeno k soukromému poli třídy.  
  
- `CalendarExists`soukromá metoda, která vrací logickou hodnotu, která označuje, zda je kalendář reprezentovaný objektem `CalendarUtility` podporován objektem <xref:System.Globalization.CultureInfo>, který je předán metodě jako parametr. Metoda zabalí volání metody <xref:System.Array.Exists%2A?displayProperty=nameWithType>, do které předává pole <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType>.  
  
- `HasSameName`, soukromá metoda přiřazená delegátu <xref:System.Predicate%601>, která je předána jako parametr metodě <xref:System.Array.Exists%2A?displayProperty=nameWithType>. Každý člen pole je předán metodě, dokud metoda nevrátí `true`. Metoda určuje, zda je název volitelného kalendáře stejný jako kalendář reprezentovaný objektem `CalendarUtility`.  
  
- `DisplayDate`, přetížená veřejná metoda, která je předána dvěma parametrům: hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset>, která má být vyjádřena v kalendáři reprezentovaném objektem `CalendarUtility`; a jazykovou verzi, jejíž pravidla formátování se mají použít. Chování při vrácení řetězcové reprezentace data závisí na tom, zda je cílový kalendář podporován jazykovou verzí, jejíž pravidla formátování mají být použita.  
  
 Bez ohledu na kalendář použitý k vytvoření hodnoty <xref:System.DateTime> nebo <xref:System.DateTimeOffset> v tomto příkladu je tato hodnota obvykle vyjádřena jako gregoriánské datum. Důvodem je to, že typy <xref:System.DateTime> a <xref:System.DateTimeOffset> neuchovávají žádné informace v kalendáři. Interně jsou reprezentovány jako počet taktů, které uplynuly od půlnoci 1. ledna 0001. Výklad tohoto čísla závisí na kalendáři. Pro většinu kultur je výchozím kalendářem gregoriánský kalendář.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
