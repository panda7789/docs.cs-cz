---
title: "Postupy: Extrahování dne v týdnu z konkrétního data"
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
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET Framework], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET Framework], day of week
- Weekday function
- day of week [.NET Framework]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET Framework], day of week
- formatting [.NET Framework], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3accb01eb8c5edb8b3e245020b43c5a94a8bb4cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="e8484-102">Postupy: Extrahování dne v týdnu z konkrétního data</span><span class="sxs-lookup"><span data-stu-id="e8484-102">How to: Extract the Day of the Week from a Specific Date</span></span>
<span data-ttu-id="e8484-103">Rozhraní .NET Framework usnadňuje určení pořadí dne v týdnu pro konkrétní datum a zobrazí se název lokalizované den v týdnu pro konkrétní datum.</span><span class="sxs-lookup"><span data-stu-id="e8484-103">The .NET Framework makes it easy to determine the ordinal day of the week for a particular date, and to display the localized weekday name for a particular date.</span></span> <span data-ttu-id="e8484-104">Výčtová hodnota určující, den v týdnu odpovídající konkrétní datum je k dispozici prostřednictvím <xref:System.DateTime.DayOfWeek%2A> nebo <xref:System.DateTimeOffset.DayOfWeek%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8484-104">An enumerated value that indicates the day of the week corresponding to a particular date is available from the <xref:System.DateTime.DayOfWeek%2A> or <xref:System.DateTimeOffset.DayOfWeek%2A> property.</span></span> <span data-ttu-id="e8484-105">Načítání názvu den v týdnu je naopak operaci formátování, které lze provést pomocí volání metody pro formátování, jako je například hodnota data a času `ToString` metoda nebo <xref:System.String.Format%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="e8484-105">In contrast, retrieving the weekday name is a formatting operation that can be performed by calling a formatting method, such as a date and time value's `ToString` method or the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e8484-106">Toto téma ukazuje, jak provést tyto operace formátování.</span><span class="sxs-lookup"><span data-stu-id="e8484-106">This topic shows how to perform these formatting operations.</span></span>  
  
### <a name="to-extract-a-number-indicating-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="e8484-107">Extrahování číslo určující den v týdnu z konkrétního data</span><span class="sxs-lookup"><span data-stu-id="e8484-107">To extract a number indicating the day of the week from a specific date</span></span>  
  
1.  <span data-ttu-id="e8484-108">Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8484-108">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="e8484-109">Použití <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti načíst <xref:System.DayOfWeek> hodnotu, která označuje den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="e8484-109">Use the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve a <xref:System.DayOfWeek> value that indicates the day of the week.</span></span>  
  
3.  <span data-ttu-id="e8484-110">V případě potřeby přetypování (v C#) nebo převést (v jazyce Visual Basic) <xref:System.DayOfWeek> hodnotu na celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e8484-110">If necessary, cast (in C#) or convert (in Visual Basic) the <xref:System.DayOfWeek> value to an integer.</span></span>  
  
 <span data-ttu-id="e8484-111">Následující příklad zobrazí celé číslo představující den v týdnu konkrétní datum.</span><span class="sxs-lookup"><span data-stu-id="e8484-111">The following example displays an integer that represents the day of the week of a specific date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
### <a name="to-extract-the-abbreviated-weekday-name-from-a-specific-date"></a><span data-ttu-id="e8484-112">Extrahovat zkrácený název dne z konkrétního data</span><span class="sxs-lookup"><span data-stu-id="e8484-112">To extract the abbreviated weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="e8484-113">Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8484-113">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="e8484-114">Můžete rozbalit zkrácený název dne aktuální jazykové verze nebo konkrétní jazykové verze:</span><span class="sxs-lookup"><span data-stu-id="e8484-114">You can extract the abbreviated weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="e8484-115">Chcete-li extrahovat zkrácený název dne pro aktuální jazykovou verzi, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodu instance a předejte řetězec "ddd" jako `format` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-115">To extract the abbreviated weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="e8484-116">Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="e8484-116">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2.  <span data-ttu-id="e8484-117">Chcete-li extrahovat zkrácený název dne pro konkrétní jazykové verze, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance.</span><span class="sxs-lookup"><span data-stu-id="e8484-117">To extract the abbreviated weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="e8484-118">Předejte řetězec "ddd" jako `format` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-118">Pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="e8484-119">Buď předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který reprezentuje jazykovou verzi, jejíž název den v týdnu, můžete obnovit jako `provider` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-119">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="e8484-120">Následující kód ukazuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který reprezentuje fr-FR jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e8484-120">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the fr-FR culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
### <a name="to-extract-the-full-weekday-name-from-a-specific-date"></a><span data-ttu-id="e8484-121">Chcete-li extrahovat název úplné den v týdnu z konkrétního data</span><span class="sxs-lookup"><span data-stu-id="e8484-121">To extract the full weekday name from a specific date</span></span>  
  
1.  <span data-ttu-id="e8484-122">Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8484-122">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="e8484-123">Můžete rozbalit úplné den v týdnu název aktuální jazykové verze nebo konkrétní jazykové verze:</span><span class="sxs-lookup"><span data-stu-id="e8484-123">You can extract the full weekday name of the current culture or of a specific culture:</span></span>  
  
    1.  <span data-ttu-id="e8484-124">Chcete-li extrahovat úplný název pro aktuální jazykovou verzi, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metodu instance a předejte řetězec "dddd" jako `format` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-124">To extract the weekday name for the current culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="e8484-125">Následující příklad ukazuje volání <xref:System.DateTime.ToString%28System.String%29> metoda.</span><span class="sxs-lookup"><span data-stu-id="e8484-125">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2.  <span data-ttu-id="e8484-126">Chcete-li extrahovat úplný název pro konkrétní jazykové verze, volejte hodnota data a času <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> metodu instance.</span><span class="sxs-lookup"><span data-stu-id="e8484-126">To extract the weekday name for a specific culture, call the date and time value’s <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="e8484-127">Předejte řetězec "dddd" jako `format` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-127">Pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="e8484-128">Buď předat <xref:System.Globalization.CultureInfo> nebo <xref:System.Globalization.DateTimeFormatInfo> objekt, který reprezentuje jazykovou verzi, jejíž název den v týdnu, můžete obnovit jako `provider` parametr.</span><span class="sxs-lookup"><span data-stu-id="e8484-128">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="e8484-129">Následující kód ukazuje volání <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> pomocí metody <xref:System.Globalization.CultureInfo> objekt, který reprezentuje es-ES jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e8484-129">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the es-ES culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="e8484-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8484-130">Example</span></span>  
 <span data-ttu-id="e8484-131">Tento příklad ukazuje volání <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> vlastnosti a <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> a <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> metody pro získání čísla, které představuje den v týdnu, zkrácený název dne a názvu úplné den v týdnu pro konkrétní datum.</span><span class="sxs-lookup"><span data-stu-id="e8484-131">The example illustrates calls to the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> properties and the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> methods to retrieve the number that represents the day of the week, the abbreviated weekday name, and the full weekday name for a particular date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 <span data-ttu-id="e8484-132">Jednotlivé jazyky může poskytují funkce, která duplikuje nebo doplňují funkce poskytované službou [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e8484-132">Individual languages may provide functionality that duplicates or supplements the functionality provided by the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="e8484-133">Visual Basic například obsahuje dvě takové funkce:</span><span class="sxs-lookup"><span data-stu-id="e8484-133">For example, Visual Basic includes two such functions:</span></span>  
  
-   <span data-ttu-id="e8484-134">`Weekday`, která vrací číslo, které označuje den v týdnu určitého data.</span><span class="sxs-lookup"><span data-stu-id="e8484-134">`Weekday`, which returns a number that indicates the day of the week of a particular date.</span></span> <span data-ttu-id="e8484-135">Považuje za pořadové číslo první den v týdnu na jednu, zatímco <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost považuje být nula.</span><span class="sxs-lookup"><span data-stu-id="e8484-135">It considers the ordinal value of the first day of the week to be one, whereas the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property considers it to be zero.</span></span>  
  
-   <span data-ttu-id="e8484-136">`WeekdayName`, která vrací název v týdnu v aktuální jazykovou verzi, která odpovídá na číslo určitý den v týdnu.</span><span class="sxs-lookup"><span data-stu-id="e8484-136">`WeekdayName`, which returns the name of the week in the current culture that corresponds to a particular weekday number.</span></span>  
  
 <span data-ttu-id="e8484-137">Následující příklad ukazuje použití Visual Basicu `Weekday` a `WeekdayName` funkce.</span><span class="sxs-lookup"><span data-stu-id="e8484-137">The following example illustrates the use of the Visual Basic `Weekday` and `WeekdayName` functions.</span></span>  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <span data-ttu-id="e8484-138">Můžete také použít hodnoty vrácené <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> vlastnost načíst název den v týdnu určitého data.</span><span class="sxs-lookup"><span data-stu-id="e8484-138">You can also use the value returned by the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve the weekday name of a particular date.</span></span> <span data-ttu-id="e8484-139">To vyžaduje pouze volání <xref:System.Enum.ToString%2A> metodu <xref:System.DayOfWeek> hodnoty vrácené vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8484-139">This requires only a call to the <xref:System.Enum.ToString%2A> method on the <xref:System.DayOfWeek> value returned by the property.</span></span> <span data-ttu-id="e8484-140">Tento postup však neobsahuje název lokalizované den v týdnu pro aktuální jazykovou verzi, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8484-140">However, this technique does not produce a localized weekday name for the current culture, as the following example illustrates.</span></span>  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="e8484-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8484-141">See Also</span></span>  
 [<span data-ttu-id="e8484-142">Provádění operací formátování</span><span class="sxs-lookup"><span data-stu-id="e8484-142">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="e8484-143">Řetězce formátu standardní hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="e8484-143">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="e8484-144">Řetězce formátu vlastní hodnota data a času</span><span class="sxs-lookup"><span data-stu-id="e8484-144">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
