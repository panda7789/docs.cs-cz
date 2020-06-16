---
title: Analýza řetězců v .NET
description: Porozumění analýze řetězců v .NET. Při analýze se převede řetězec reprezentující základní typ .NET do tohoto základního typu. Analýza je operace zpětného formátování.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: 5e297c8f689fdabc268ee6e269a7969155befe7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769285"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="d6e4d-105">Analýza řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="d6e4d-105">Parsing Strings in .NET</span></span>
<span data-ttu-id="d6e4d-106">Operace analýzy převede řetězec, který představuje základní typ .NET, do tohoto základního typu.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-106">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="d6e4d-107">Například operace analýzy slouží k převodu řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-107">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="d6e4d-108">Metoda, která se nejčastěji používá k provedení operace analýzy, je `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-108">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="d6e4d-109">Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcové vyjádření), platí celá řada stejných pravidel a konvencí.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-109">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="d6e4d-110">Stejně jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k poskytnutí informací o formátování zohledňující jazykovou verzi, analýza také používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k určení, jak interpretovat řetězcovou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-110">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="d6e4d-111">Další informace najdete v článku o [typech formátování](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d6e4d-111">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6e4d-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d6e4d-112">In This Section</span></span>  
 [<span data-ttu-id="d6e4d-113">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="d6e4d-113">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="d6e4d-114">Popisuje, jak převést řetězce na číselné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-114">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="d6e4d-115">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="d6e4d-115">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="d6e4d-116">Popisuje, jak převést řetězce na typy **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-116">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="d6e4d-117">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="d6e4d-117">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="d6e4d-118">Popisuje, jak převést řetězce na typy **char**, **Boolean**a **Enum** .</span><span class="sxs-lookup"><span data-stu-id="d6e4d-118">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6e4d-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d6e4d-119">Related Sections</span></span>  
 [<span data-ttu-id="d6e4d-120">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="d6e4d-120">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="d6e4d-121">Popisuje základní koncepty formátování, jako jsou specifikátory formátu a poskytovatelé formátu.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-121">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="d6e4d-122">Převod typu v .NET</span><span class="sxs-lookup"><span data-stu-id="d6e4d-122">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="d6e4d-123">Popisuje, jak převést typy.</span><span class="sxs-lookup"><span data-stu-id="d6e4d-123">Describes how to convert types.</span></span>
