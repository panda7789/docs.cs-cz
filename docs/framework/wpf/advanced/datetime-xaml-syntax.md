---
title: "DateTime – syntaxe v jazyce XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DateTime XAML syntax [WPF], strings for
- DateTime XAML syntax [WPF], where used
- short date format [WPF], DateTime
- DateTime XAML syntax [WPF]
- DateTime XAML text [WPF]
- DateTime XAML syntax [WPF], format strings for
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e261018e6c7b9fea9ad449c5e92a131df40807
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="datetime-xaml-syntax"></a><span data-ttu-id="84c11-102">DateTime – syntaxe v jazyce XAML</span><span class="sxs-lookup"><span data-stu-id="84c11-102">DateTime XAML Syntax</span></span>
<span data-ttu-id="84c11-103">Některé ovládací prvky, jako například <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>, mít vlastnosti, které používají <xref:System.DateTime> typu.</span><span class="sxs-lookup"><span data-stu-id="84c11-103">Some controls, such as <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>, have properties that use the <xref:System.DateTime> type.</span></span> <span data-ttu-id="84c11-104">I když obvykle zadejte počáteční datum nebo čas pro tyto ovládací prvky v kódu v době běhu je zadat v jazyce XAML počáteční datum nebo čas.</span><span class="sxs-lookup"><span data-stu-id="84c11-104">Although you typically specify an initial date or time for these controls in the code-behind at run time, you can specify an initial date or time in XAML.</span></span> <span data-ttu-id="84c11-105">Analyzátor WPF XAML zpracovává analýze <xref:System.DateTime> hodnoty pomocí předdefinovaných syntaxe text XAML.</span><span class="sxs-lookup"><span data-stu-id="84c11-105">The WPF XAML parser handles parsing of <xref:System.DateTime> values using a built-in XAML text syntax.</span></span> <span data-ttu-id="84c11-106">Toto téma popisuje, jaké jsou specifikace <xref:System.DateTime> XAML textových syntaxi.</span><span class="sxs-lookup"><span data-stu-id="84c11-106">This topic describes the specifics of the <xref:System.DateTime> XAML text syntax.</span></span>  
  
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## <a name="when-to-use-datetime-xaml-syntax"></a><span data-ttu-id="84c11-107">Při použití syntaxe XAML data a času</span><span class="sxs-lookup"><span data-stu-id="84c11-107">When To Use DateTime XAML Syntax</span></span>  
 <span data-ttu-id="84c11-108">Nastavení kalendářních dat v jazyce XAML není vždy nutné a dokonce nemusí být žádoucí.</span><span class="sxs-lookup"><span data-stu-id="84c11-108">Setting dates in XAML is not always necessary and may not even be desirable.</span></span> <span data-ttu-id="84c11-109">Například můžete použít <xref:System.DateTime.Now%2A?displayProperty=nameWithType> vlastnost inicializovat data v době běhu, nebo můžete udělat všechny datum úpravy pro kalendář v kódu založené na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="84c11-109">For example, you could use the <xref:System.DateTime.Now%2A?displayProperty=nameWithType> property to initialize a date at run time, or you could do all your date adjustments for a calendar in the code-behind based on user input.</span></span> <span data-ttu-id="84c11-110">Ale existují scénáře, kde můžete data pevný kódu do <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker> v šabloně ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="84c11-110">However, there are scenarios where you may want to hard-code dates into a <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker> in a control template.</span></span> <span data-ttu-id="84c11-111"><xref:System.DateTime> XAML syntaxe musí být použita pro tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="84c11-111">The <xref:System.DateTime> XAML syntax must be used for these scenarios.</span></span>  
  
### <a name="datetime-xaml-syntax-is-a-native-behavior"></a><span data-ttu-id="84c11-112">Syntaxe jazyka XAML data a času je nativní chování</span><span class="sxs-lookup"><span data-stu-id="84c11-112">DateTime XAML Syntax is a Native Behavior</span></span>  
 <span data-ttu-id="84c11-113"><xref:System.DateTime>je třída, která je definována v knihovnách základní třídy modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="84c11-113"><xref:System.DateTime> is a class that is defined in the base class libraries of the CLR.</span></span> <span data-ttu-id="84c11-114">Z důvodu jak základní třídy knihovny vztahují k zbytek modulu CLR, není možné použít <xref:System.ComponentModel.TypeConverterAttribute> třídy a používání převaděče typů ke zpracování řetězců z XAML a převést tak, aby <xref:System.DateTime> v době běhu objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="84c11-114">Because of how the base class libraries relate to the rest of the CLR, it is not possible to apply <xref:System.ComponentModel.TypeConverterAttribute> to the class and use a type converter to process strings from XAML and convert them to <xref:System.DateTime> in the run time object model.</span></span> <span data-ttu-id="84c11-115">Neexistuje žádné `DateTimeConverter` – třída, která poskytuje chování převod; převod chování popsané v tomto tématu je nativní pro analyzátor WPF XAML.</span><span class="sxs-lookup"><span data-stu-id="84c11-115">There is no `DateTimeConverter` class that provides the conversion behavior; the conversion behavior described in this topic is native to the WPF XAML parser.</span></span>  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## <a name="format-strings-for-datetime-xaml-syntax"></a><span data-ttu-id="84c11-116">Řetězce formátu data a času XAML syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c11-116">Format Strings for DateTime XAML Syntax</span></span>  
 <span data-ttu-id="84c11-117">Můžete zadat formát <xref:System.DateTime> s řetězci formátu.</span><span class="sxs-lookup"><span data-stu-id="84c11-117">You can specify the format of a <xref:System.DateTime> with a format string.</span></span> <span data-ttu-id="84c11-118">Řetězce formátu formalizujte syntaxe text, který slouží k vytvoření hodnoty.</span><span class="sxs-lookup"><span data-stu-id="84c11-118">Format strings formalize the text syntax that can be used to create a value.</span></span> <span data-ttu-id="84c11-119"><xref:System.DateTime>hodnoty pro existující WPF řídí obecně pouze použití datum součástí <xref:System.DateTime> a není součástí čas.</span><span class="sxs-lookup"><span data-stu-id="84c11-119"><xref:System.DateTime> values for the existing WPF controls generally only use the date components of <xref:System.DateTime> and not the time components.</span></span>  
  
 <span data-ttu-id="84c11-120">Při zadávání <xref:System.DateTime> v jazyce XAML, můžete použít některý z řetězce formátu zcela zaměnitelným významem.</span><span class="sxs-lookup"><span data-stu-id="84c11-120">When specifying a <xref:System.DateTime> in XAML, you can use any of the format strings interchangeably.</span></span>  
  
 <span data-ttu-id="84c11-121">Můžete také použít formáty a formát řetězce, které nejsou konkrétně zobrazeny v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="84c11-121">You can also use formats and format strings that are not specifically shown in this topic.</span></span> <span data-ttu-id="84c11-122">Technicky XAML pro žádné <xref:System.DateTime> hodnotu, která je zadána a potom analyzovat analyzátorem jazyka XAML WPF používá interní volání <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, proto můžete použít libovolný řetězec, který bude přijímat <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> pro váš jazyk XAML vstup.</span><span class="sxs-lookup"><span data-stu-id="84c11-122">Technically, the XAML for any <xref:System.DateTime> value that is specified and then parsed by the WPF XAML parser uses an internal  call to <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>, therefore you could use any string accepted by <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> for your XAML input.</span></span> <span data-ttu-id="84c11-123">Další informace naleznete v tématu <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84c11-123">For more information, see <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84c11-124">Syntaxe jazyka XAML data a času vždy používá `en-us` jako <xref:System.Globalization.CultureInfo> pro jeho nativní převod.</span><span class="sxs-lookup"><span data-stu-id="84c11-124">The DateTime XAML syntax always uses `en-us` as the <xref:System.Globalization.CultureInfo> for its native conversion.</span></span> <span data-ttu-id="84c11-125">Toto není ovlivněné <xref:System.Windows.FrameworkElement.Language%2A> hodnotu nebo `xml:lang` hodnoty v jazyce XAML, protože převod XAML úroveň atributu typu funguje bez tohoto kontextu.</span><span class="sxs-lookup"><span data-stu-id="84c11-125">This is not influenced by <xref:System.Windows.FrameworkElement.Language%2A> value or `xml:lang` value in the XAML, because XAML attribute-level type conversion acts without that context.</span></span> <span data-ttu-id="84c11-126">Nepokoušejte se promítnout řetězce formátu kvůli kulturního změny, jako jsou pořadí, ve kterém dne a měsíce zobrazí tady uvedené.</span><span class="sxs-lookup"><span data-stu-id="84c11-126">Do not attempt to interpolate the format strings shown here due to cultural variations, such as the order in which day and month appear.</span></span> <span data-ttu-id="84c11-127">Řetězce formátu vidět tady jsou řetězce přesném formátu, který použije při analýze XAML bez ohledu na ostatní nastavení jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="84c11-127">The format strings shown here are the exact format strings used when parsing the XAML regardless of other culture settings.</span></span>  
  
 <span data-ttu-id="84c11-128">Následující části popisují některé nejběžnější <xref:System.DateTime> řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="84c11-128">The following sections describe some of the common <xref:System.DateTime> format strings.</span></span>  
  
### <a name="short-date-pattern-d"></a><span data-ttu-id="84c11-129">Vzoru krátkého data ("d")</span><span class="sxs-lookup"><span data-stu-id="84c11-129">Short Date Pattern ("d")</span></span>  
 <span data-ttu-id="84c11-130">Následující příklad zobrazuje formát krátkého data <xref:System.DateTime> v jazyce XAML:</span><span class="sxs-lookup"><span data-stu-id="84c11-130">The following shows the short date format for a <xref:System.DateTime> in XAML:</span></span>  
  
 `M/d/YYYY`  
  
 <span data-ttu-id="84c11-131">Toto je nejjednodušší podobě Určuje všechny potřebné informace pro typické použití ovládacích prvků WPF a nemůže mít vliv náhodných časových pásmech versus komponentu dobu a proto se doporučuje namísto jiných formátů.</span><span class="sxs-lookup"><span data-stu-id="84c11-131">This is the simplest form that specifies all necessary information for typical usages by WPF controls, and cannot be influenced by accidental time zone offsets versus a time component, and is therefore recommended over the other formats.</span></span>  
  
 <span data-ttu-id="84c11-132">Například zadejte datum 1. června 2010, použijte následující řetězec:</span><span class="sxs-lookup"><span data-stu-id="84c11-132">For example, to specify the date of June 1, 2010, use the following string:</span></span>  
  
 `3/1/2010`  
  
 <span data-ttu-id="84c11-133">Další informace naleznete v tématu <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84c11-133">For more information, see <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="sortable-datetime-pattern-s"></a><span data-ttu-id="84c11-134">Řazení vzor data a času ("s")</span><span class="sxs-lookup"><span data-stu-id="84c11-134">Sortable DateTime Pattern ("s")</span></span>  
 <span data-ttu-id="84c11-135">Následující příklad zobrazuje seřaditelný <xref:System.DateTime> vzoru v jazyce XAML:</span><span class="sxs-lookup"><span data-stu-id="84c11-135">The following shows the sortable <xref:System.DateTime> pattern in XAML:</span></span>  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 <span data-ttu-id="84c11-136">Například zadejte datum 1. června 2010, použijte následující řetězec (čas, které součásti jsou zadali jako 0):</span><span class="sxs-lookup"><span data-stu-id="84c11-136">For example, to specify the date of June 1, 2010, use the following string (time components are all entered as 0):</span></span>  
  
 `2010-06-01T000:00:00`  
  
### <a name="rfc1123-pattern-r"></a><span data-ttu-id="84c11-137">Vzor RFC1123 ("r")</span><span class="sxs-lookup"><span data-stu-id="84c11-137">RFC1123 Pattern ("r")</span></span>  
 <span data-ttu-id="84c11-138">Vzor RFC1123 je užitečné, protože by mohlo být vstup řetězce z jiné datum generátory, kteří také používají vzor RFC1123 důvodů neutrální jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="84c11-138">The RFC1123 pattern is useful because it could be a string input from other date generators that also use the RFC1123 pattern for culture invariant reasons.</span></span> <span data-ttu-id="84c11-139">Následující příklad zobrazuje RFC1123 <xref:System.DateTime> vzoru v jazyce XAML:</span><span class="sxs-lookup"><span data-stu-id="84c11-139">The following shows the RFC1123 <xref:System.DateTime> pattern in XAML:</span></span>  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 <span data-ttu-id="84c11-140">Například zadejte datum 1. června 2010, použijte následující řetězec (čas, které součásti jsou zadali jako 0):</span><span class="sxs-lookup"><span data-stu-id="84c11-140">For example, to specify the date of June 1, 2010, use the following string (time components are all entered as 0):</span></span>  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### <a name="other-formats-and-patterns"></a><span data-ttu-id="84c11-141">Ostatní formáty a vzorce</span><span class="sxs-lookup"><span data-stu-id="84c11-141">Other Formats and Patterns</span></span>  
 <span data-ttu-id="84c11-142">Jak jsme uvedli dříve, <xref:System.DateTime> v jazyce XAML, lze zadat jako libovolný řetězec, který se dá použít jako vstupní pro <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84c11-142">As stated previously, a <xref:System.DateTime> in XAML can be specified as any string that is acceptable as input for <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84c11-143">To zahrnuje dalších formalizovanou formátů (například <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>) a formáty, které nejsou stanovení jako konkrétní <xref:System.Globalization.DateTimeFormatInfo> formuláře.</span><span class="sxs-lookup"><span data-stu-id="84c11-143">This includes other formalized formats (for example <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>), and formats that are not formalized as a particular <xref:System.Globalization.DateTimeFormatInfo> form.</span></span> <span data-ttu-id="84c11-144">Například formulář `YYYY/mm/dd` je přijatelné pro jako vstupní <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="84c11-144">For example, the form `YYYY/mm/dd` is acceptable as input for <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="84c11-145">Toto téma se nebude pokoušet popisují všechny možné formáty, které fungovat a místo toho doporučuje vzoru krátkého data z hlediska standardní.</span><span class="sxs-lookup"><span data-stu-id="84c11-145">This topic does not attempt to describe all possible formats that work, and instead recommends the short date pattern as a standard practice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c11-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="84c11-146">See Also</span></span>  
 [<span data-ttu-id="84c11-147">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="84c11-147">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
