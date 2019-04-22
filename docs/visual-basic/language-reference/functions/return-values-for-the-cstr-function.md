---
title: Návratové hodnoty pro funkci CStr (Visual Basic)
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
ms.openlocfilehash: 3653194c7e48533e664ac7513ca7f4f48d1c69f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819512"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a><span data-ttu-id="bce9c-102">Návratové hodnoty pro funkci CStr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bce9c-102">Return Values for the CStr Function (Visual Basic)</span></span>
<span data-ttu-id="bce9c-103">Následující tabulka popisuje vrácené hodnoty `CStr` pro různé datové typy `expression`.</span><span class="sxs-lookup"><span data-stu-id="bce9c-103">The following table describes the return values for `CStr` for different data types of `expression`.</span></span>  
  
|<span data-ttu-id="bce9c-104">Pokud `expression` je typ</span><span class="sxs-lookup"><span data-stu-id="bce9c-104">If `expression` type is</span></span>|<span data-ttu-id="bce9c-105">`CStr` Vrátí</span><span class="sxs-lookup"><span data-stu-id="bce9c-105">`CStr` returns</span></span>|  
|-----------------------------|--------------------|  
|[<span data-ttu-id="bce9c-106">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="bce9c-106">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="bce9c-107">Řetězec obsahující "True" nebo "Nepravda".</span><span class="sxs-lookup"><span data-stu-id="bce9c-107">A string containing "True" or "False".</span></span>|  
|[<span data-ttu-id="bce9c-108">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="bce9c-108">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="bce9c-109">Řetězec obsahující `Date` hodnota (datum a čas) ve formátu krátkého data vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="bce9c-109">A string containing a `Date` value (date and time) in the short date format of your system.</span></span>|  
|[<span data-ttu-id="bce9c-110">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="bce9c-110">Numeric Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|<span data-ttu-id="bce9c-111">Řetězec představující číslo.</span><span class="sxs-lookup"><span data-stu-id="bce9c-111">A string representing the number.</span></span>|  
  
## <a name="cstr-and-date"></a><span data-ttu-id="bce9c-112">CStr data a času</span><span class="sxs-lookup"><span data-stu-id="bce9c-112">CStr and Date</span></span>  
 <span data-ttu-id="bce9c-113">`Date` Typ vždy obsahuje informace o datu a času.</span><span class="sxs-lookup"><span data-stu-id="bce9c-113">The `Date` type always contains both date and time information.</span></span> <span data-ttu-id="bce9c-114">Pro účely převodů, Visual Basic považuje za 1/1/0001 (od 1. ledna roku 1) *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) bude neutrální hodnota pro dobu.</span><span class="sxs-lookup"><span data-stu-id="bce9c-114">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="bce9c-115">`CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci.</span><span class="sxs-lookup"><span data-stu-id="bce9c-115">`CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="bce9c-116">Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00: 00"; informace o datu je potlačeno.</span><span class="sxs-lookup"><span data-stu-id="bce9c-116">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="bce9c-117">Informace o datu je však stále k dispozici v původní `Date` hodnotu a je možné obnovit pomocí funkcí, jako <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span><span class="sxs-lookup"><span data-stu-id="bce9c-117">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bce9c-118">`CStr` Funkce provádí její převod na základě nastavení aktuální jazykové verze pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bce9c-118">The `CStr` function performs its conversion based on the current culture settings for the application.</span></span> <span data-ttu-id="bce9c-119">K získání řetězcové vyjádření čísla v konkrétní jazykovou verzi, použijte číslo `ToString(IFormatProvider)` metody.</span><span class="sxs-lookup"><span data-stu-id="bce9c-119">To get the string representation of a number in a particular culture, use the number's `ToString(IFormatProvider)` method.</span></span> <span data-ttu-id="bce9c-120">Například použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` k `String`.</span><span class="sxs-lookup"><span data-stu-id="bce9c-120">For example, use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bce9c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bce9c-121">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [<span data-ttu-id="bce9c-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="bce9c-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bce9c-123">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="bce9c-123">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="bce9c-124">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="bce9c-124">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)
