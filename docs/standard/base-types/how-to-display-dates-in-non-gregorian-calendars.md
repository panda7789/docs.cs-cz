---
title: "Postupy: Zobrazování dat v jiném než gregoriánském kalendáři"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a79860091e549dcf4eaa7090947f9506eceb6119
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Postupy: Zobrazování dat v jiném než gregoriánském kalendáři
<xref:System.DateTime> a <xref:System.DateTimeOffset> typy používají gregoriánský kalendář jako svůj výchozí kalendář. To znamená, že volání hodnota data a času `ToString` metoda zobrazí řetězcovou reprezentaci datum a čas v gregoriánském kalendáři, i když je datum a čas vytvoření pomocí jiného kalendáře. To je znázorněno v následujícím příkladu, který používá dva různé způsoby vytvoření hodnoty data a času pomocí perského kalendáře, ale stále zobrazuje tyto hodnoty data a času v gregoriánském kalendáři při volání <xref:System.DateTime.ToString%2A> metoda. Tento příklad zobrazuje dvě techniky běžně používané, ale nesprávné zobrazování data v určitém kalendáři.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Dvě různé metody slouží k zobrazení data v určitém kalendáři. První vyžaduje, aby kalendáře výchozí kalendář pro konkrétní jazykové verzi. Druhý lze použít s libovolným kalendářem.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Chcete-li zobrazit datum kalendáře výchozí jazykové verze  
  
1.  Vytvoření instance objektu kalendáře odvozeného z <xref:System.Globalization.Calendar> třídu, která představuje kalendář, který se má použít.  
  
2.  Vytváření instancí <xref:System.Globalization.CultureInfo> objekt představující jazykovou verzi, jejíž formátování se použije k zobrazení data.  
  
3.  Volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metoda k určení, zda je objekt kalendáře členem poli vráceném <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> vlastnost. To znamená, že kalendář může sloužit jako výchozí kalendář pro <xref:System.Globalization.CultureInfo> objektu. Pokud není členem pole, postupujte podle pokynů v části "K zobrazení the data v libovolném kalendáři".  
  
4.  Přiřaďte objekt kalendář, který má <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> vlastnost <xref:System.Globalization.DateTimeFormatInfo> objekt vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost.  
  
    > [!NOTE]
    >  <xref:System.Globalization.CultureInfo> Třída také obsahuje <xref:System.Globalization.CultureInfo.Calendar%2A> vlastnost. Je však jen pro čtení a konstantní. tak, aby odrážely novou výchozí kalendář přiřazený k nezmění <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost.  
  
5.  Volání buď <xref:System.DateTime.ToString%2A> nebo <xref:System.DateTime.ToString%2A> metoda, možností a předejte ji <xref:System.Globalization.CultureInfo> objekt, jehož výchozí kalendář byla upravena v předchozím kroku.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Zobrazí datum v libovolném kalendáři  
  
1.  Vytvoření instance objektu kalendáře odvozeného z <xref:System.Globalization.Calendar> třídu, která představuje kalendář, který se má použít.  
  
2.  Určit, které datum a čas elementy by se měla objevit v řetězcovou reprezentaci hodnoty data a času.  
  
3.  Pro každý prvek datum a čas, který chcete zobrazit volání objektu kalendáře `Get`... Metoda. Jsou dostupné tyto metody:  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, zobrazíte v roce v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, chcete-li zobrazit v měsíci v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, chcete-li zobrazit počet den v měsíci v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, chcete-li zobrazit hodiny dne v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, chcete-li zobrazit za minut za hodinu v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, chcete-li zobrazit do sekund za minutu v příslušném kalendáři.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>, chcete-li zobrazit milisekundy za sekundu v příslušném kalendáři.  
  
## <a name="example"></a>Příklad  
 V příkladu se zobrazí datum pomocí dvou různých kalendářů. Zobrazuje datum, po definování kalendáře hidžra jako výchozí kalendář pro jazykovou verzi ar JO a zobrazuje datum Perském kalendáři, který není podporován jako volitelný kalendář DM IR jazykovou verzi.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Každý <xref:System.Globalization.CultureInfo> objekt může podporovat jeden nebo více kalendářů, která jsou zobrazena <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> vlastnost. Jedním z nich je určený jako výchozí kalendář pro jazykovou verzi a vrátí jen pro čtení <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> vlastnost. Další volitelné kalendářů lze označit jako výchozí přiřazením <xref:System.Globalization.Calendar> objekt, který reprezentuje tento kalendář, který <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> vlastnost vrácený <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> vlastnost. Ale některé kalendáře, jako je například perský kalendář reprezentovaný <xref:System.Globalization.PersianCalendar> třídy, neslouží jako volitelný kalendář pro všechny jazykové verze.  
  
 Příklad definuje třídu nástrojů opakovaně použitelné kalendář, `CalendarUtility`, aby zpracoval mnoho podrobností generování řetězcovou reprezentaci data pomocí určitého kalendáře. `CalendarUtility` Třída má následující členy:  
  
-   Parametrizovaný konstruktor, jehož jeden parametr je <xref:System.Globalization.Calendar> objektu, ve kterém má být reprezentován datum. To je přiřazený k soukromé pole třídy.  
  
-   `CalendarExists`, soukromá metoda, která vrací logickou hodnotu udávající, zda kalendáře reprezentována `CalendarUtility` je podporován <xref:System.Globalization.CultureInfo> objekt, který je předaný metodě jako parametr. Metoda zabalí volání <xref:System.Array.Exists%2A?displayProperty=nameWithType> metody, které předá <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> pole.  
  
-   `HasSameName`, soukromá metoda přiřazená k <xref:System.Predicate%601> delegáta, který se předá jako parametr, který se <xref:System.Array.Exists%2A?displayProperty=nameWithType> metoda. Každý člen pole je předán metodu, dokud vrátí metoda `true`. Metoda určuje, zda je název volitelného kalendáře stejný jako kalendář reprezentována `CalendarUtility` objektu.  
  
-   `DisplayDate`, přetížené veřejné metody, který je předán dva parametry: buď <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu express v kalendáři reprezentována `CalendarUtility` objekt; a jazykovou verzi, jejíž pravidla formátování mají být použita. Vrací řetězec představující datum jeho chování závisí na tom, jestli je cílový kalendář podporován jazykovou verzi, jejíž pravidla formátování mají být použita.  
  
 Bez ohledu na použitý k vytvoření kalendáře <xref:System.DateTime> nebo <xref:System.DateTimeOffset> hodnotu v tomto příkladu, že hodnota je obvykle vyjádřený jako gregoriánského. Důvodem je, že <xref:System.DateTime> a <xref:System.DateTimeOffset> typy nezachováte všech informací z kalendáře. Interně jsou reprezentovány jako počet značek, které uplynuly od půlnoci 1. ledna 0001. Výklad toto číslo závisí na kalendáři. Pro většinu jazykových verzí je výchozí kalendář gregoriánském kalendáři.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje odkaz na System.Core.dll.  
  
 Je možné zkompilovat kód v příkazovém řádku pomocí souboru csc.exe nebo vb.exe. Chcete-li kód zkompilovat v rámci [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vložte jej do šablony projektu konzolové aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Provádění operací formátování](../../../docs/standard/base-types/performing-formatting-operations.md)
