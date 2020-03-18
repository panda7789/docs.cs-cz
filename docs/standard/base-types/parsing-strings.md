---
title: Analýza řetězců v rozhraní .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: e4bf14981e538d95aebac3b0f36d38b61747989f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73084318"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="80e8f-102">Analýza řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="80e8f-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="80e8f-103">Operace analýzy převede řetězec, který představuje základní typ .NET na tento základní typ.</span><span class="sxs-lookup"><span data-stu-id="80e8f-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="80e8f-104">Například operace analýzy se používá k převodu řetězce na číslo s plovoucí desetinnou tácem nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="80e8f-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="80e8f-105">Metoda nejčastěji používaná k provedení operace analýzy je `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="80e8f-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="80e8f-106">Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcovou reprezentaci), platí mnoho stejných pravidel a konvencí.</span><span class="sxs-lookup"><span data-stu-id="80e8f-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="80e8f-107">Stejně jako formátování používá objekt, <xref:System.IFormatProvider> který implementuje rozhraní k poskytování informací o formátování citlivé na <xref:System.IFormatProvider> jazykovou verzi, analýza také používá objekt, který implementuje rozhraní k určení, jak interpretovat reprezentaci řetězce.</span><span class="sxs-lookup"><span data-stu-id="80e8f-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="80e8f-108">Další informace najdete v článku o [typech formátování](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="80e8f-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="80e8f-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="80e8f-109">In This Section</span></span>  
 [<span data-ttu-id="80e8f-110">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="80e8f-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="80e8f-111">Popisuje převod řetězců na číselné typy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="80e8f-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="80e8f-112">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="80e8f-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="80e8f-113">Popisuje, jak převést řetězce na typy .NET **DateTime.**</span><span class="sxs-lookup"><span data-stu-id="80e8f-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="80e8f-114">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="80e8f-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="80e8f-115">Popisuje, jak převést řetězce na **typy Char**, **Boolean**a **Enum.**</span><span class="sxs-lookup"><span data-stu-id="80e8f-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="80e8f-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="80e8f-116">Related Sections</span></span>  
 [<span data-ttu-id="80e8f-117">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="80e8f-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="80e8f-118">Popisuje základní koncepty formátování, jako jsou specifikátory formátu a zprostředkovatelé formátů.</span><span class="sxs-lookup"><span data-stu-id="80e8f-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="80e8f-119">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="80e8f-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="80e8f-120">Popisuje, jak převést typy.</span><span class="sxs-lookup"><span data-stu-id="80e8f-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="80e8f-121">Základní typy</span><span class="sxs-lookup"><span data-stu-id="80e8f-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="80e8f-122">Popisuje běžné operace, které lze provádět na základních typech rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="80e8f-122">Describes common operations that you can perform on .NET base types.</span></span>
