---
title: "Date – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190b40888dc4a42075b7b6b27bdb1bd403a7efb5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="2e8fe-102">Date – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e8fe-102">Date Data Type (Visual Basic)</span></span>
<span data-ttu-id="2e8fe-103">Obsahuje hodnoty IEEE 64-bit (8 bajtů), které reprezentují rozsahu od 1. ledna roku 0001 až 31. prosince 9999 roku datum a čas od 12:00:00: 00 (půlnoc) prostřednictvím 11:59:59.9999999 PM.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="2e8fe-104">Každý přírůstek představuje 100 nanosekundách uplynulý čas od začátku 1. ledna roku 1 v gregoriánském kalendáři.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="2e8fe-105">Maximální hodnota 100 nanosekundách představuje před začátkem 1. ledna roku 10000.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e8fe-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e8fe-106">Remarks</span></span>  
 <span data-ttu-id="2e8fe-107">Použití `Date` datový typ obsahovat hodnoty data, času hodnoty nebo hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>  
  
 <span data-ttu-id="2e8fe-108">Výchozí hodnota `Date` je 0:00:00 (půlnoc) na 1. ledna 0001.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>  
  
 <span data-ttu-id="2e8fe-109">Můžete získat aktuální datum a čas z <xref:Microsoft.VisualBasic.DateAndTime> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="2e8fe-110">Požadavky na formát</span><span class="sxs-lookup"><span data-stu-id="2e8fe-110">Format Requirements</span></span>  
 <span data-ttu-id="2e8fe-111">Je nutné uzavřít `Date` literálu v rámci znaky (`# #`).</span><span class="sxs-lookup"><span data-stu-id="2e8fe-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="2e8fe-112">Zadejte hodnoty date ve formátu M/d/rrrr, například `#5/31/1993#`, nebo RRRR MM-dd, například `#1993-5-31#`.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="2e8fe-113">Lomítka můžete použít při zadávání nejprve v roce.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="2e8fe-114">Tento požadavek je nezávislý na národním prostředí, data počítače a nastavení formátu času.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>  
  
 <span data-ttu-id="2e8fe-115">Důvod tohoto omezení je, že význam kódu by nikdy změnit v závislosti na národním prostředí, ve kterém je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="2e8fe-116">Předpokládejme, pevné kódu `Date` literálu z `#3/4/1998#` a chcete-li znamenat 4. března 1998.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="2e8fe-117">V národním prostředí, která používá mm/dd/rrrr 3 nebo 4 nebo 1998 zkompiluje jako, který chcete.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="2e8fe-118">Ale Předpokládejme, že nasazení aplikace v mnoha zemích.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-118">But suppose you deploy your application in many countries.</span></span> <span data-ttu-id="2e8fe-119">V národním prostředí, která používá dd/mm/rrrr by do 3. dubna 1998 zkompilovat vaší pevně literál.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="2e8fe-120">V národním prostředí, která používá rrrr/mm/dd, by byl neplatný literál (duben 1998 0003) a způsobit chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>  
  
## <a name="workarounds"></a><span data-ttu-id="2e8fe-121">Alternativní řešení</span><span class="sxs-lookup"><span data-stu-id="2e8fe-121">Workarounds</span></span>  
 <span data-ttu-id="2e8fe-122">Převést `Date` literál formát národní prostředí, nebo vlastní formát, zadejte literál k <xref:Microsoft.VisualBasic.Strings.Format%2A> funkce, zadání buď formátu předdefinovaných nebo uživatelsky definovaných data.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="2e8fe-123">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-123">The following example demonstrates this.</span></span>  
  
```  
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))  
```  
  
 <span data-ttu-id="2e8fe-124">Alternativně můžete použít jednu z přetížené konstruktory <xref:System.DateTime> struktura ke kompilaci hodnota data a času.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="2e8fe-125">Následující příklad vytvoří hodnotu představující 31 může 1993 na 12:14 odpoledne.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>  
  
```  
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)  
```  
  
## <a name="hour-format"></a><span data-ttu-id="2e8fe-126">H formátu</span><span class="sxs-lookup"><span data-stu-id="2e8fe-126">Hour Format</span></span>  
 <span data-ttu-id="2e8fe-127">Hodnota času ve formátu 12 hodin nebo 24 hodin, můžete zadat například `#1:15:30 PM#` nebo `#13:15:30#`.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="2e8fe-128">Ale pokud nezadáte dobu nebo do sekund, zadejte dop.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>  
  
## <a name="date-and-time-defaults"></a><span data-ttu-id="2e8fe-129">Datum a čas výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="2e8fe-129">Date and Time Defaults</span></span>  
 <span data-ttu-id="2e8fe-130">Pokud nebudou obsahovat datum v literálu datum/čas, Visual Basic nastaví datum součástí hodnotu 1. ledna 0001.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="2e8fe-131">Pokud nezadáte čas v literál datum a čas, Visual Basic nastaví časovou část hodnoty na začátek dne, který je půlnoc (0: 00:00).</span><span class="sxs-lookup"><span data-stu-id="2e8fe-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="2e8fe-132">Převody typu</span><span class="sxs-lookup"><span data-stu-id="2e8fe-132">Type Conversions</span></span>  
 <span data-ttu-id="2e8fe-133">Pokud převedete `Date` hodnotu `String` typu, vykreslí datum podle formát krátkého data určeného národní prostředí runtime jazyka Visual Basic a vykreslí čas podle formát času (12 hodin nebo 24 hodin) určeného národní prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="2e8fe-134">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="2e8fe-134">Programming Tips</span></span>  
  
-   <span data-ttu-id="2e8fe-135">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="2e8fe-135">**Interop Considerations.**</span></span> <span data-ttu-id="2e8fe-136">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, která data a času typy v jiných prostředích nejsou kompatibilní s jazykem Visual Basic `Date` typu.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="2e8fe-137">Pokud tyto součásti jsou předány argumentem datum a čas, deklarujte ji jako `Double` místo `Date` v jazyce Visual Basic kód a použít metody převod <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="2e8fe-138">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="2e8fe-138">**Type Characters.**</span></span> <span data-ttu-id="2e8fe-139">`Date`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="2e8fe-140">Ale kompilátor zpracovává literály uzavřené v rámci znaky (`# #`) jako `Date`.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>  
  
-   <span data-ttu-id="2e8fe-141">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="2e8fe-141">**Framework Type.**</span></span> <span data-ttu-id="2e8fe-142">Typ odpovídající v rozhraní .NET Framework je <xref:System.DateTime?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e8fe-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e8fe-143">Example</span></span>  
 <span data-ttu-id="2e8fe-144">Proměnnou nebo konstantu `Date` obsahuje datový typ datum a čas.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="2e8fe-145">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2e8fe-145">The following example illustrates this.</span></span>  
  
```  
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e8fe-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e8fe-146">See Also</span></span>  
 <xref:System.DateTime?displayProperty=nameWithType>  
 [<span data-ttu-id="2e8fe-147">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2e8fe-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2e8fe-148">Řetězce formátu standardní hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="2e8fe-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)  
 [<span data-ttu-id="2e8fe-149">Řetězce formátu vlastní hodnota data a času</span><span class="sxs-lookup"><span data-stu-id="2e8fe-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)  
 [<span data-ttu-id="2e8fe-150">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="2e8fe-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2e8fe-151">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="2e8fe-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2e8fe-152">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="2e8fe-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
