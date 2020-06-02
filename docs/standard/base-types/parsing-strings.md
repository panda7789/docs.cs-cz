---
title: Analýza řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
ms.openlocfilehash: ab446a8f868cabdeff73d1b72e1399b7c2beb1e1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277411"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="cdaf7-102">Analýza řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="cdaf7-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="cdaf7-103">Operace analýzy převede řetězec, který představuje základní typ .NET, do tohoto základního typu.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="cdaf7-104">Například operace analýzy slouží k převodu řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="cdaf7-105">Metoda, která se nejčastěji používá k provedení operace analýzy, je `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="cdaf7-106">Vzhledem k tomu, že analýza je reverzní operace formátování (která zahrnuje převod základního typu na jeho řetězcové vyjádření), platí celá řada stejných pravidel a konvencí.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="cdaf7-107">Stejně jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k poskytnutí informací o formátování zohledňující jazykovou verzi, analýza také používá objekt, který implementuje <xref:System.IFormatProvider> rozhraní k určení, jak interpretovat řetězcovou reprezentaci.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="cdaf7-108">Další informace najdete v článku o [typech formátování](formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="cdaf7-108">For more information, see [Formatting Types](formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdaf7-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cdaf7-109">In This Section</span></span>  
 [<span data-ttu-id="cdaf7-110">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="cdaf7-110">Parsing Numeric Strings</span></span>](parsing-numeric.md)  
 <span data-ttu-id="cdaf7-111">Popisuje, jak převést řetězce na číselné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="cdaf7-112">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="cdaf7-112">Parsing Date and Time Strings</span></span>](parsing-datetime.md)  
 <span data-ttu-id="cdaf7-113">Popisuje, jak převést řetězce na typy **DateTime** .NET.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="cdaf7-114">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="cdaf7-114">Parsing Other Strings</span></span>](parsing-other.md)  
 <span data-ttu-id="cdaf7-115">Popisuje, jak převést řetězce na typy **char**, **Boolean**a **Enum** .</span><span class="sxs-lookup"><span data-stu-id="cdaf7-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cdaf7-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cdaf7-116">Related Sections</span></span>  
 [<span data-ttu-id="cdaf7-117">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="cdaf7-117">Formatting Types</span></span>](formatting-types.md)  
 <span data-ttu-id="cdaf7-118">Popisuje základní koncepty formátování, jako jsou specifikátory formátu a poskytovatelé formátu.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="cdaf7-119">Převod typu v .NET</span><span class="sxs-lookup"><span data-stu-id="cdaf7-119">Type Conversion in .NET</span></span>](type-conversion.md)  
 <span data-ttu-id="cdaf7-120">Popisuje, jak převést typy.</span><span class="sxs-lookup"><span data-stu-id="cdaf7-120">Describes how to convert types.</span></span>
