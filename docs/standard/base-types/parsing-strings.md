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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6e0e7e69affd93320ec3f3d73e6254befaf6ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765996"
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="3a0d5-102">Analýza řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="3a0d5-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="3a0d5-103">Operace analýzy převede řetězec, který představuje základní typ formátu .NET do základního typu.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="3a0d5-104">Například operace analýzy slouží k převedení řetězce na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="3a0d5-105">Metoda nejčastěji používá k provedení operace analýzy je `Parse` metody.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="3a0d5-106">Protože je analýza reverzní operaci formátování (který zahrnuje převod základního typu na jeho řetězcovou reprezentaci), řadu stejných pravidel a konvence použít.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="3a0d5-107">Stejně jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> poskytovat informace formátování zohledňující jazykovou verzi, analýze také používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> rozhraní zjistěte, jak interpretovat řetězcové vyjádření .</span><span class="sxs-lookup"><span data-stu-id="3a0d5-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="3a0d5-108">Další informace najdete v tématu [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="3a0d5-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a0d5-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3a0d5-109">In This Section</span></span>  
 [<span data-ttu-id="3a0d5-110">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="3a0d5-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="3a0d5-111">Popisuje, jak převod řetězců na numerické typy .NET.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="3a0d5-112">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="3a0d5-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="3a0d5-113">Popisuje, jak převod řetězců na .NET **data a času** typy.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="3a0d5-114">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="3a0d5-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="3a0d5-115">Popisuje, jak převést řetězců do **Char**, **logická**, a **výčtu** typy.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a0d5-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3a0d5-116">Related Sections</span></span>  
 [<span data-ttu-id="3a0d5-117">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="3a0d5-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="3a0d5-118">Popisuje základní principy formátování jako specifikátory formátu a poskytovatelů formátu.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="3a0d5-119">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3a0d5-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="3a0d5-120">Popisuje, jak převod typů.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="3a0d5-121">Základní typy</span><span class="sxs-lookup"><span data-stu-id="3a0d5-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="3a0d5-122">Popisuje běžné operace, které můžete provádět na základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="3a0d5-122">Describes common operations that you can perform on .NET base types.</span></span>
