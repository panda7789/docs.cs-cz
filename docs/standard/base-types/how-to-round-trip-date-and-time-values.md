---
title: "Postupy: Hodnoty data a času round-trip"
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="04929-102">Postupy: Hodnoty data a času round-trip</span><span class="sxs-lookup"><span data-stu-id="04929-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="04929-103">V mnoha aplikacích hodnota data a času je určený pro jednoznačnou identifikaci jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="04929-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="04929-104">Toto téma ukazuje, jak k uložení a obnovení <xref:System.DateTime> hodnotu, <xref:System.DateTimeOffset> hodnota a datum a čas hodnotu s časem zónu informace tak, aby obnovená hodnota identifikuje ve stejnou dobu jako uložena hodnota.</span><span class="sxs-lookup"><span data-stu-id="04929-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="04929-105">Operace round-trip pro hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="04929-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="04929-106">Převést <xref:System.DateTime> hodnotu na řetězcovou reprezentaci voláním <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> metoda s specifikátor formátu "o".</span><span class="sxs-lookup"><span data-stu-id="04929-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="04929-107">Uložte řetězcovou reprezentaci <xref:System.DateTime> hodnoty do souboru, nebo ji předejte procesu, aplikační domény nebo počítač hranici.</span><span class="sxs-lookup"><span data-stu-id="04929-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="04929-108">Načíst řetězec, který představuje <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="04929-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="04929-109">Volání <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metoda a předejte jí <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametr.</span><span class="sxs-lookup"><span data-stu-id="04929-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="04929-110">Následující příklad ukazuje, jak k odezvě <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="04929-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="04929-111">Když odezvy <xref:System.DateTime> hodnotu, tato technika úspěšně zachová čas pro všechny místního a univerzálního časy.</span><span class="sxs-lookup"><span data-stu-id="04929-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="04929-112">Například, pokud místní <xref:System.DateTime> hodnota je uložena v systému v USA Tichomořském časovém pásmu a obnovení systému v USA Střed standardního časového pásma, obnovené datum a čas bude později než původní čas, což odráží časový rozdíl mezi dvěma časových pásem dvě hodiny.</span><span class="sxs-lookup"><span data-stu-id="04929-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="04929-113">Tento postup však není nutně přesný pro neurčené časy.</span><span class="sxs-lookup"><span data-stu-id="04929-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="04929-114">Všechny <xref:System.DateTime> hodnoty, jehož <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Unspecified> jsou zpracovány jako v případě, že jsou místních časů.</span><span class="sxs-lookup"><span data-stu-id="04929-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="04929-115">Pokud to tak není, <xref:System.DateTime> nebude úspěšně identifikovat správný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="04929-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="04929-116">Alternativní řešení pro toto omezení je úzce spojte hodnota data a času s časovým pásmem pro uložení a operaci obnovení.</span><span class="sxs-lookup"><span data-stu-id="04929-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="04929-117">Operace round-trip pro hodnotu DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="04929-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="04929-118">Převést <xref:System.DateTimeOffset> hodnotu na řetězcovou reprezentaci voláním <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> metoda s specifikátor formátu "o".</span><span class="sxs-lookup"><span data-stu-id="04929-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="04929-119">Uložte řetězcovou reprezentaci <xref:System.DateTimeOffset> hodnoty do souboru, nebo ji předejte procesu, aplikační domény nebo počítač hranici.</span><span class="sxs-lookup"><span data-stu-id="04929-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="04929-120">Načíst řetězec, který představuje <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="04929-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="04929-121">Volání <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> metoda a předejte jí <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> jako hodnotu `styles` parametr.</span><span class="sxs-lookup"><span data-stu-id="04929-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="04929-122">Následující příklad ukazuje, jak k odezvě <xref:System.DateTimeOffset> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="04929-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="04929-123">Tato technika vždy jednoznačně identifikuje <xref:System.DateTimeOffset> hodnotu jako jediný bod v čase.</span><span class="sxs-lookup"><span data-stu-id="04929-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="04929-124">Hodnota pak může být převedena na koordinovaný světový čas (UTC) voláním <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> metoda, nebo může být převeden na čas v určitém časovém pásmu voláním <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> nebo <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="04929-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="04929-125">Hlavním omezením Tato technika je datum a čas aritmetické operace, při provádění v <xref:System.DateTimeOffset> hodnotu, která reprezentuje čas v určitém časovém pásmu, nemusí poskytovat přesné výsledky pro toto časové pásmo.</span><span class="sxs-lookup"><span data-stu-id="04929-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="04929-126">Důvodem je, že když <xref:System.DateTimeOffset> vytváření instance hodnoty, je časovému pásmu, jeho.</span><span class="sxs-lookup"><span data-stu-id="04929-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="04929-127">Proto pravidla úpravy časového pásma můžete už použijí při provádění výpočtů datum a čas.</span><span class="sxs-lookup"><span data-stu-id="04929-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="04929-128">Tento problém můžete vyřešit definováním vlastního typu, který obsahuje datum a čas hodnota a jejich příslušná časová pásma.</span><span class="sxs-lookup"><span data-stu-id="04929-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="04929-129">Operace round-trip pro hodnoty data a času s časovým pásmem</span><span class="sxs-lookup"><span data-stu-id="04929-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="04929-130">Definujte třídu nebo strukturu se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="04929-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="04929-131">První pole je buď <xref:System.DateTime> nebo <xref:System.DateTimeOffset> objekt a druhá je <xref:System.TimeZoneInfo> objektu.</span><span class="sxs-lookup"><span data-stu-id="04929-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="04929-132">V následujícím příkladu je jednoduchý verze takového typu.</span><span class="sxs-lookup"><span data-stu-id="04929-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="04929-133">Označte třídu <xref:System.SerializableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="04929-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="04929-134">Serializovat objekt pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="04929-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="04929-135">Obnovení pomocí objektu <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="04929-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="04929-136">Přetypování (v C#) nebo převést (v jazyce Visual Basic) deserializovaný objekt na objekt příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="04929-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="04929-137">Následující příklad ilustruje, jak k odezvě na objekt, který ukládá informace o datu a času a časového pásma.</span><span class="sxs-lookup"><span data-stu-id="04929-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="04929-138">Tento postup by měl vždy odrážet bod správný čas i před a po jeho uložení a obnovení, zadaný, implementace objektu kombinované datum a čas a časové pásmo nepovoluje hodnoty date se synchronizované s Hodnota časového pásma.</span><span class="sxs-lookup"><span data-stu-id="04929-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04929-139">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="04929-139">Compiling the Code</span></span>  
 <span data-ttu-id="04929-140">Tyto příklady vyžadují:</span><span class="sxs-lookup"><span data-stu-id="04929-140">These examples require:</span></span>  
  
-   <span data-ttu-id="04929-141">Že následujících oborů názvů naimportovat pomocí C# `using` příkazy nebo [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` příkazy:</span><span class="sxs-lookup"><span data-stu-id="04929-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="04929-142"><xref:System>(C# pouze).</span><span class="sxs-lookup"><span data-stu-id="04929-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="04929-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04929-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="04929-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04929-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="04929-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04929-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="04929-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="04929-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="04929-147">Odkaz na System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="04929-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="04929-148">Každý příklad kódu, než `DateInTimeZone` třídy, by měl zahrnuté ve třídě nebo modulu Visual Basic, uzavřen do metod a volání z `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="04929-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04929-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="04929-149">See Also</span></span>  
 [<span data-ttu-id="04929-150">Provádění operací formátování</span><span class="sxs-lookup"><span data-stu-id="04929-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="04929-151">Volba mezi DateTime, DateTimeOffset, TimeSpan a TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="04929-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="04929-152">Řetězce formátu standardní hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="04929-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
