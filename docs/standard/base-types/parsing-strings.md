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
ms.openlocfilehash: 717022e5d2e292c1624e6155bd7571e4daa997b9
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523806"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="7081d-102">Analýza řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="7081d-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="7081d-103">Operace analýzy převede řetězec, který představuje základní typ .NET na tento základní typ.</span><span class="sxs-lookup"><span data-stu-id="7081d-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="7081d-104">Například operace analýzy se používá k převodu řetězce na číslo s plovoucí desetinnou tácem nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="7081d-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="7081d-105">Metoda nejčastěji používaná k provedení operace analýzy je `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="7081d-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="7081d-106">Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcovou reprezentaci), platí mnoho stejných pravidel a konvencí.</span><span class="sxs-lookup"><span data-stu-id="7081d-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="7081d-107">Stejně jako formátování používá objekt, <xref:System.IFormatProvider> který implementuje rozhraní k poskytování informací o formátování citlivé na <xref:System.IFormatProvider> jazykovou verzi, analýza také používá objekt, který implementuje rozhraní k určení, jak interpretovat reprezentaci řetězce.</span><span class="sxs-lookup"><span data-stu-id="7081d-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="7081d-108">Další informace najdete v článku o [typech formátování](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="7081d-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7081d-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7081d-109">In This Section</span></span>  
 [<span data-ttu-id="7081d-110">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="7081d-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="7081d-111">Popisuje převod řetězců na číselné typy rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7081d-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="7081d-112">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="7081d-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="7081d-113">Popisuje, jak převést řetězce na typy .NET **DateTime.**</span><span class="sxs-lookup"><span data-stu-id="7081d-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="7081d-114">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="7081d-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="7081d-115">Popisuje, jak převést řetězce na **typy Char**, **Boolean**a **Enum.**</span><span class="sxs-lookup"><span data-stu-id="7081d-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7081d-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7081d-116">Related Sections</span></span>  
 [<span data-ttu-id="7081d-117">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="7081d-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="7081d-118">Popisuje základní koncepty formátování, jako jsou specifikátory formátu a zprostředkovatelé formátů.</span><span class="sxs-lookup"><span data-stu-id="7081d-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="7081d-119">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="7081d-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="7081d-120">Popisuje, jak převést typy.</span><span class="sxs-lookup"><span data-stu-id="7081d-120">Describes how to convert types.</span></span>
