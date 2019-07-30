---
title: Date – datový typ (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: ee966cdfcc957f1164c73f577fa668b203a82113
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630117"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="481de-102">Date – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="481de-102">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="481de-103">Obsahuje hodnoty IEEE 64 (8 bajtů), které reprezentují data od 1. ledna do 31. prosince 9999 a časy od 12:00:00 (půlnoc) do 11:59:59.9999999 ODP.</span><span class="sxs-lookup"><span data-stu-id="481de-103">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="481de-104">Každý přírůstek představuje 100 nanosekund, uplynulý čas od začátku 1. ledna v roce 1 v gregoriánském kalendáři.</span><span class="sxs-lookup"><span data-stu-id="481de-104">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="481de-105">Maximální hodnota představuje 100 nanosekund před začátkem 1. ledna v roce 10000.</span><span class="sxs-lookup"><span data-stu-id="481de-105">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="481de-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="481de-106">Remarks</span></span>

<span data-ttu-id="481de-107">`Date` Datový typ použijte k zahrnutí hodnot data, času nebo hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="481de-107">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="481de-108">Výchozí hodnota `Date` je 0:00:00 (půlnoc) od 1. ledna 0001.</span><span class="sxs-lookup"><span data-stu-id="481de-108">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="481de-109">Aktuální datum a čas můžete získat z <xref:Microsoft.VisualBasic.DateAndTime> třídy.</span><span class="sxs-lookup"><span data-stu-id="481de-109">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="481de-110">Požadavky na formát</span><span class="sxs-lookup"><span data-stu-id="481de-110">Format Requirements</span></span>

<span data-ttu-id="481de-111">Je nutné uzavřít `Date` literál v rámci znaménka čísla (`# #`).</span><span class="sxs-lookup"><span data-stu-id="481de-111">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="481de-112">Je třeba zadat hodnotu data ve formátu M/d/rrrr, `#5/31/1993#`například nebo rrrr-mm-dd, `#1993-5-31#`například.</span><span class="sxs-lookup"><span data-stu-id="481de-112">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="481de-113">Při prvním zadání roku můžete použít lomítka.</span><span class="sxs-lookup"><span data-stu-id="481de-113">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="481de-114">Tento požadavek nezávisí na vašem národním prostředí a na nastavení formátu data a času vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="481de-114">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="481de-115">Důvodem tohoto omezení je, že význam vašeho kódu by se nikdy neměl měnit v závislosti na národním prostředí, ve kterém je vaše aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="481de-115">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="481de-116">Předpokládejme, že máte pevně zavedený `#3/4/1998#` kód `Date` literálu a máte v úmyslu do 4. března 1998.</span><span class="sxs-lookup"><span data-stu-id="481de-116">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="481de-117">V národním prostředí, které používá mm/dd/rrrr, se 3/4/1998 zkompiluje jako zamýšlená.</span><span class="sxs-lookup"><span data-stu-id="481de-117">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="481de-118">Ale Předpokládejme, že nasadíte aplikaci v mnoha zemích nebo oblastech.</span><span class="sxs-lookup"><span data-stu-id="481de-118">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="481de-119">V národním prostředí, které používá dd/mm/rrrr, je pevně zakódovaný literál zkompilován do 3. dubna 1998.</span><span class="sxs-lookup"><span data-stu-id="481de-119">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="481de-120">V národním prostředí, které používá rrrr/mm/dd, bude literál neplatný (duben 1998, 0003) a způsobit chybu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="481de-120">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="481de-121">Alternativní řešení</span><span class="sxs-lookup"><span data-stu-id="481de-121">Workarounds</span></span>

<span data-ttu-id="481de-122">Chcete-li `Date` převést literál na formát národního prostředí nebo na vlastní formát, zadejte do <xref:Microsoft.VisualBasic.Strings.Format%2A> funkce literál a zadejte buď předdefinovaný nebo uživatelsky definovaný formát data.</span><span class="sxs-lookup"><span data-stu-id="481de-122">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="481de-123">Následující příklad ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="481de-123">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="481de-124">Alternativně můžete použít jeden z přetížených konstruktorů <xref:System.DateTime> struktury k sestavení hodnoty data a času.</span><span class="sxs-lookup"><span data-stu-id="481de-124">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="481de-125">Následující příklad vytvoří hodnotu, která představuje 31. května 1993 v 12:14 za odpoledne.</span><span class="sxs-lookup"><span data-stu-id="481de-125">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="481de-126">Formát hodiny</span><span class="sxs-lookup"><span data-stu-id="481de-126">Hour Format</span></span>

<span data-ttu-id="481de-127">Hodnotu času můžete zadat buď v 12 hodinách, nebo ve 24hodinovém formátu, například `#1:15:30 PM#` nebo. `#13:15:30#`</span><span class="sxs-lookup"><span data-stu-id="481de-127">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="481de-128">Pokud však nezadáte buď minuty, nebo sekundy, je nutné zadat dop nebo PM.</span><span class="sxs-lookup"><span data-stu-id="481de-128">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="481de-129">Výchozí hodnoty data a času</span><span class="sxs-lookup"><span data-stu-id="481de-129">Date and Time Defaults</span></span>

<span data-ttu-id="481de-130">Pokud nezahrnete datum do literálu data a času, Visual Basic nastaví část hodnoty data na 1. ledna 0001.</span><span class="sxs-lookup"><span data-stu-id="481de-130">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="481de-131">Pokud nezahrnete čas do literálu data a času, Visual Basic nastaví časovou část hodnoty na začátek dne, tj. půlnoc (0:00:00).</span><span class="sxs-lookup"><span data-stu-id="481de-131">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="481de-132">Převody typu</span><span class="sxs-lookup"><span data-stu-id="481de-132">Type Conversions</span></span>

<span data-ttu-id="481de-133">Převedete `Date` -li hodnotu `String` na typ, Visual Basic vykreslí datum podle formátu krátkého data určeného národním prostředím runtime a vykreslí čas podle formátu času (12 hodin nebo 24 hodin) určeného parametrem národní prostředí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="481de-133">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="481de-134">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="481de-134">Programming Tips</span></span>

- <span data-ttu-id="481de-135">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="481de-135">**Interop Considerations.**</span></span> <span data-ttu-id="481de-136">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte na to, že typy data a času v jiných prostředích nejsou kompatibilní s `Date` typem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="481de-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="481de-137">Pokud předáváte argument typu datum/čas pro takovou komponentu, deklarujte ji jako `Double` `Date` místo v novém Visual Basic kódu a použijte metody <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> převodu a <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="481de-137">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="481de-138">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="481de-138">**Type Characters.**</span></span> <span data-ttu-id="481de-139">`Date`nemá žádný znak typu literálu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="481de-139">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="481de-140">Nicméně kompilátor zpracovává literály, které jsou uzavřeny v symbolech`# #`čísla ( `Date`) jako.</span><span class="sxs-lookup"><span data-stu-id="481de-140">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="481de-141">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="481de-141">**Framework Type.**</span></span> <span data-ttu-id="481de-142">Odpovídající typ v .NET Framework je <xref:System.DateTime?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="481de-142">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="481de-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="481de-143">Example</span></span>

<span data-ttu-id="481de-144">Proměnná nebo konstanta `Date` datového typu obsahuje datum i čas.</span><span class="sxs-lookup"><span data-stu-id="481de-144">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="481de-145">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="481de-145">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="481de-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="481de-146">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="481de-147">Datové typy</span><span class="sxs-lookup"><span data-stu-id="481de-147">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="481de-148">Standardní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="481de-148">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="481de-149">Vlastní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="481de-149">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="481de-150">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="481de-150">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="481de-151">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="481de-151">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="481de-152">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="481de-152">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
