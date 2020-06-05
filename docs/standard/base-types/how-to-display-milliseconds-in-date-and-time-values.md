---
title: 'Postupy: Zobrazení milisekund v hodnotách data a času'
description: V tomto článku se dozvíte, jak zahrnout komponentu milisekund data a času ve formátovaných řetězcích data a času v .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
ms.openlocfilehash: a6dbe6a3bf4f8c08493ec925bea4316d071f4182
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447066"
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="4a9d1-103">Postupy: Zobrazení milisekund v hodnotách data a času</span><span class="sxs-lookup"><span data-stu-id="4a9d1-103">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="4a9d1-104">Výchozí metody pro formátování hodnot data a času, jako například <xref:System.DateTime.ToString?displayProperty=nameWithType>, zahrnují hodiny, minuty a sekundy příslušné časové hodnoty, ale neobsahují komponentu milisekund.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-104">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="4a9d1-105">Toto téma popisuje způsob začlenění komponenty milisekund do příslušné hodnoty data a času ve formátovaných řetězcích data a času.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-105">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="4a9d1-106">Zobrazení komponenty milisekund hodnoty DateTime</span><span class="sxs-lookup"><span data-stu-id="4a9d1-106">To display the millisecond component of a DateTime value</span></span>  
  
1. <span data-ttu-id="4a9d1-107">Při práci s řetězcovou reprezentací data je třeba ji převést na hodnotu <xref:System.DateTime> nebo <xref:System.DateTimeOffset> pomocí statické metody <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-107">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="4a9d1-108">Chcete-li extrahovat řetězcovou reprezentaci komponenty milisekund, zavolejte metodu hodnot data a času <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> nebo <xref:System.DateTimeOffset.ToString%2A> a předejte vzor vlastního formátu `fff` nebo `FFF` buď samostatně, nebo s dalšími specifikátory vlastního formátu jako parametr `format`.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-108">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a9d1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a9d1-109">Example</span></span>  
 <span data-ttu-id="4a9d1-110">Příklad zobrazí komponentu milisekund hodnot <xref:System.DateTime> a <xref:System.DateTimeOffset> do konzoly samostatně i jako součást delšího řetězce data a času.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-110">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="4a9d1-111">Vzor formátu `fff` zahrnuje všechny koncové nuly v hodnotě milisekund.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-111">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="4a9d1-112">Vzor formátu `FFF` je potlačí.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-112">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="4a9d1-113">Rozdíl je znázorněn v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-113">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="4a9d1-114">Problém s definováním kompletního specifikátoru vlastního formátu, který zahrnuje komponentu milisekund příslušného data a času, spočívá v tom, že definuje pevně zakódovaný formát, který nemusí odpovídat uspořádání prvků času v aktuální jazykové verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-114">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="4a9d1-115">Lepší alternativou je načíst jeden ze vzorů zobrazení data a času, které jsou definovány v objektu aktuální jazykové verze <xref:System.Globalization.DateTimeFormatInfo>, a upravit je tak, aby milisekundy obsahovaly.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-115">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="4a9d1-116">Tento příklad znázorňuje také tento přístup.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-116">The example also illustrates this approach.</span></span> <span data-ttu-id="4a9d1-117">Načte úplný vzor data a času pro aktuální jazykovou verzi z vlastnosti <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> a poté za vzor sekund vloží vlastní vzor `.ffff`.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-117">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="4a9d1-118">Příklad používá pro provedení této operace v rámci jednoho volání metody regulární výraz.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-118">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="4a9d1-119">Pro zobrazení jiné části sekundového údaje než milisekund lze použít také specifikátor vlastního formátu.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-119">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="4a9d1-120">Například specifikátor vlastního formátu `f` nebo `F` zobrazí desetiny sekundy, specifikátor vlastního formátu `ff` nebo `FF` zobrazí setiny sekundy a specifikátor vlastního formátu `ffff` nebo `FFFF` zobrazí desetitisíciny sekundy.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-120">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="4a9d1-121">Zlomkové části milisekundy jsou ve vráceném řetězci namísto zaokrouhlení zkráceny.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-121">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="4a9d1-122">Tyto specifikátory formátu se používají v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-122">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="4a9d1-123">Je možné zobrazit velmi malé zlomkové jednotky sekundy, jako například desetitisíciny sekundy nebo stotisíciny sekundy.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-123">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="4a9d1-124">Tyto hodnoty však nemusí být smysluplné.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-124">However, these values may not be meaningful.</span></span> <span data-ttu-id="4a9d1-125">Přesnost hodnot data a času závisí na rozlišení systémových hodin.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-125">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="4a9d1-126">V operačních systémech Windows NT 3,5 a novějších a Windows Vista je rozlišení hodin přibližně 10-15 milisekund.</span><span class="sxs-lookup"><span data-stu-id="4a9d1-126">On Windows NT 3.5 and later, and Windows Vista operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9d1-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a9d1-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="4a9d1-128">Vlastní řetězce formátu data a času</span><span class="sxs-lookup"><span data-stu-id="4a9d1-128">Custom Date and Time Format Strings</span></span>](custom-date-and-time-format-strings.md)
