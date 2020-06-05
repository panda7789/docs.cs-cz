---
title: Návratové hodnoty pro funkci CStr
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 6039ba3f6bd1c364db818807604ee0851bc23d50
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406381"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="915f7-102">Návratové hodnoty pro funkci CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="915f7-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="915f7-103">V následující tabulce jsou popsány návratové hodnoty pro `CStr` různé datové typy `expression` .</span><span class="sxs-lookup"><span data-stu-id="915f7-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="915f7-104">Pokud `expression` typ je</span><span class="sxs-lookup"><span data-stu-id="915f7-104">If `expression` type is</span></span>|<span data-ttu-id="915f7-105">`CStr`Vrátí</span><span class="sxs-lookup"><span data-stu-id="915f7-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="915f7-106">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="915f7-106">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="915f7-107">Řetězec obsahující "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="915f7-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="915f7-108">Date – datový typ</span><span class="sxs-lookup"><span data-stu-id="915f7-108">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="915f7-109">Řetězec obsahující `Date` hodnotu (datum a čas) v krátkém formátu data vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="915f7-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="915f7-110">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="915f7-110">Numeric Data Types</span></span>](../../programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="915f7-111">Řetězec představující číslo.</span><span class="sxs-lookup"><span data-stu-id="915f7-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="915f7-112">CStr a datum</span><span class="sxs-lookup"><span data-stu-id="915f7-112">CStr and Date</span></span>  
 <span data-ttu-id="915f7-113">`Date`Typ vždy obsahuje informace o datu a čase.</span><span class="sxs-lookup"><span data-stu-id="915f7-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="915f7-114">Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas.</span><span class="sxs-lookup"><span data-stu-id="915f7-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="915f7-115">`CStr`nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="915f7-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="915f7-116">Například Pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00 dop.", informace o datu jsou potlačeny.</span><span class="sxs-lookup"><span data-stu-id="915f7-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="915f7-117">Informace o datu jsou však stále přítomny v původní `Date` hodnotě a lze je obnovit pomocí funkcí, jako je například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> .</span><span class="sxs-lookup"><span data-stu-id="915f7-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="915f7-118">`CStr`Funkce provede svůj převod na základě aktuálního nastavení jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="915f7-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="915f7-119">Chcete-li získat řetězcové vyjádření čísla v konkrétní jazykové verzi, použijte `ToString(IFormatProvider)` metodu Number.</span><span class="sxs-lookup"><span data-stu-id="915f7-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="915f7-120">Například použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na `String` .</span><span class="sxs-lookup"><span data-stu-id="915f7-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915f7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="915f7-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="915f7-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="915f7-122">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="915f7-123">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="915f7-123">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="915f7-124">Date – datový typ</span><span class="sxs-lookup"><span data-stu-id="915f7-124">Date Data Type</span></span>](../data-types/date-data-type.md)
