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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63af71f92af9c2f3a5986dcb73f44d0e53c00f58
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871904"
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Postupy: Zobrazování dat v jiném než gregoriánském kalendáři
<xref:System.DateTime> a <xref:System.DateTimeOffset> typy používají jako výchozí kalendář gregoriánský kalendář. To znamená, že volání hodnoty data a času `ToString` metoda zobrazí řetězcové vyjádření data a času v gregoriánském kalendáři, a to i v případě, že datum a čas byl vytvořen pomocí jiného kalendáře. To je znázorněno v následujícím příkladu, který používá dva různé způsoby vytváření hodnoty data a času s perský kalendář, ale stále zobrazuje tyto hodnoty data a času v gregoriánském kalendáři, při volání <xref:System.DateTime.ToString%2A> metody. Tento příklad zobrazuje dvě techniky běžně používaný, ale nesprávné pro zobrazení data v konkrétním kalendáři.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dvě různé techniky slouží k zobrazení data v konkrétním kalendáři. První vyžaduje, aby v kalendáři výchozí kalendář pro konkrétní jazykovou verzi. Druhá jde použít s libovolný kalendář.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Chcete-li zobrazit data pro výchozí kalendář jazykové verze  
  
1.  Vytvoření instance objektu odvozené z kalendáře <xref:System.Globalization.Calendar> třídu, která představuje kalendář, který se má použít.  
  
2.  Vytvořit instanci <xref:System.Globalization.CultureInfo> objektu, který představuje jazykovou verzi, jejíž formátování se použije k zobrazení data.  
  
3.  Volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodou ke zjištění, zda je objekt kalendář členem pole vrácené metodou <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnost. To znamená, že kalendáře může sloužit jako výchozí kalendář pro <xref:System.Globalization.CultureInfo> objektu. Pokud není členem pole, postupujte podle pokynů v části "K zobrazení the data v libovolném kalendáři".  
  
4.  Přiřaďte objekt kalendář, který má <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> vlastnost <xref:System.Globalization.DateTimeFormatInfo> vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Třída má také <xref:System.Globalization.CultureInfo.Calendar%2A> vlastnost. Je ale jen pro čtení a konstantní. tak, aby odrážely nový výchozí kalendář přiřazená nezmění <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost.  
  
5.  Volání na buď <xref:System.DateTime.ToString%2A> nebo <xref:System.DateTime.ToString%2A> metoda a předat ji <xref:System.Globalization.CultureInfo> objekt, jehož výchozí kalendář byla upravena v předchozím kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Zobrazí datum v libovolný kalendář  
  
1.  Vytvoření instance objektu odvozené z kalendáře <xref:System.Globalization.Calendar> třídu, která představuje kalendář, který se má použít.  
  
2.  Určit, která data a času prvky by se měla objevit v řetězcovém vyjádření hodnoty data a času.  
  
3.  Pro každý prvek datum a čas, který chcete zobrazit volání objektu kalendáře `Get`... Metoda. Jsou dostupné tyto metody:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, zobrazí se rok v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, má zobrazit měsíc v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, chcete-li zobrazit číslo dne v měsíci v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, zobrazíte hodina dne v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, zobrazíte dobu, po které hodiny v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, zobrazíte sekund za minutu v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> , chcete-li zobrazit milisekundy za sekundu v příslušném kalendáři.  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazí datum pomocí dvou různých kalendářů. Zobrazuje datum, po definování kalendář hidžra jako výchozí kalendář pro jazykovou verzi ar JO a zobrazí datum pomocí perský kalendář, který není podporován jako volitelný kalendář jazykové verze fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Každý <xref:System.Globalization.CultureInfo> objekt může podporovat jeden nebo více kalendářů, které jsou označeny <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> vlastnost. Jeden z nich je určena jako výchozí kalendář pro jazykovou verzi a vrátí jen pro čtení <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Další volitelné kalendáře lze označit jako výchozí, přiřazením <xref:System.Globalization.Calendar> objekt, který představuje tento kalendář <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnosti vrácené <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Nicméně některé kalendáře, jako je například perský kalendář reprezentována <xref:System.Globalization.PersianCalendar> třídy, neslouží jako volitelné kalendáře žádné jazykové verze.  
  
 Příklad definuje třídu nástrojů opakovaně použitelné kalendáře, `CalendarUtility`, aby zpracoval mnoho podrobností generování řetězcovou reprezentaci data pomocí konkrétního kalendáře. `CalendarUtility` Třída má následující členy:  
  
-   Parametrizovaný konstruktor, jehož jediný parametr je <xref:System.Globalization.Calendar> objektu, ve kterém je datum a nelze je reprezentovat. To je přiřazen k soukromé pole třídy.  
  
-   `CalendarExists`, privátní metodu, která vrací logickou hodnotu označující, zda kalendář je představováno `CalendarUtility` objekt je podporován <xref:System.Globalization.CultureInfo> objekt, který se předá metodě jako parametr. Metoda zalamuje volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metodu, ke kterému předá <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> pole.  
  
-   `HasSameName`, privátní metodu přiřazené <xref:System.Predicate%601> delegáta, který je předán jako parametr, který se <xref:System.Array.Exists%2A?displayProperty=nameWithType> metoda. Každý člen pole je předán metodě, dokud metoda vrátí `true`. Metoda určuje, zda název volitelný kalendář je stejný jako kalendář reprezentována `CalendarUtility` objektu.  
  
-   `DisplayDate`, přetížené veřejné metody, která je předána dva parametry: buď <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu vyjádřit v kalendáři reprezentována `CalendarUtility` objekt; a jazykovou verzi, jejíž pravidla formátování se mají použít. Vrací řetězec představující datum jeho chování závisí na Určuje, zda cílový kalendář je podporován jazykovou verzi, jejíž pravidla formátování se mají použít.  
  
 Bez ohledu na použitý k vytvoření kalendáře <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu v tomto příkladu, že hodnota je obvykle vyjádřený jako gregoriánský kalendář. Je to proto, <xref:System.DateTime> a <xref:System.DateTimeOffset> typy Nezachovávat hodnotu informace o kalendáři. Interně jsou reprezentovány jako počet značek, které uplynuly od půlnoci 1. ledna 0001. Výklad tohoto čísla závisí na kalendář. Pro většinu jazykové verze výchozí kalendář nastaven na gregoriánský kalendář.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje odkaz na System.Core.dll.  
  
 Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe. Chcete-li zkompilovat kód v sadě Visual Studio, vložte ho do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
