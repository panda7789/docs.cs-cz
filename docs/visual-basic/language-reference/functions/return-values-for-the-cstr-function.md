---
title: "Návratové hodnoty pro funkci CStr (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="2de34-102">Návratové hodnoty pro funkci CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2de34-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="2de34-103">Následující tabulka popisuje návratové hodnoty pro `CStr` pro různé datové typy `expression`.</span><span class="sxs-lookup"><span data-stu-id="2de34-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="2de34-104">Pokud `expression` typ</span><span class="sxs-lookup"><span data-stu-id="2de34-104">If `expression` type is</span></span>|<span data-ttu-id="2de34-105">`CStr`Vrátí</span><span class="sxs-lookup"><span data-stu-id="2de34-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="2de34-106">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="2de34-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="2de34-107">Řetězec obsahující "True" nebo "Nepravda".</span><span class="sxs-lookup"><span data-stu-id="2de34-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="2de34-108">Date – datový typ</span><span class="sxs-lookup"><span data-stu-id="2de34-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="2de34-109">Řetězec obsahující `Date` hodnotu (datum a čas) ve formátu krátkého data vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="2de34-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="2de34-110">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="2de34-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="2de34-111">Řetězec představující číslo.</span><span class="sxs-lookup"><span data-stu-id="2de34-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="2de34-112">CStr data a času</span><span class="sxs-lookup"><span data-stu-id="2de34-112">CStr and Date</span></span>  
 <span data-ttu-id="2de34-113">`Date` Typ vždy obsahuje informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="2de34-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="2de34-114">Pro účely převod typů, Visual Basic považuje za 1/1/0001 (1. ledna roku 1) *neutrální hodnota* pro datum a 00:00:00 (půlnoc) se má nastavit neutrální hodnota pro dobu.</span><span class="sxs-lookup"><span data-stu-id="2de34-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="2de34-115">`CStr`nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="2de34-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="2de34-116">Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00: 00"; potlačeno informace o datu.</span><span class="sxs-lookup"><span data-stu-id="2de34-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="2de34-117">Informace o datu je však stále nachází na původní `Date` hodnotu a je možné obnovit s funkcemi, jako například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="2de34-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2de34-118">`CStr` Funkce provede jeho převodu na základě aktuální nastavení jazykové verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2de34-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="2de34-119">Řetězcová reprezentace čísla v konkrétní jazykové verzi, použijte číslo `ToString(IFormatProvider)` metoda.</span><span class="sxs-lookup"><span data-stu-id="2de34-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="2de34-120">Například použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` k `String`.</span><span class="sxs-lookup"><span data-stu-id="2de34-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de34-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2de34-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [<span data-ttu-id="2de34-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="2de34-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2de34-123">Boolean – datový typ</span><span class="sxs-lookup"><span data-stu-id="2de34-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="2de34-124">Date – datový typ</span><span class="sxs-lookup"><span data-stu-id="2de34-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
