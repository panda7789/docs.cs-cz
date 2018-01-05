---
title: "Analýza řetězců v rozhraní .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing strings, about parsing strings
- IFormatProvider interface, parsing strings
- base types, parsing strings
- Parse method
- parsing strings
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9c2193dd1b1f3c0478efb5fc9c2b80250ef1878f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-strings-in-net"></a><span data-ttu-id="cc39b-102">Analýza řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="cc39b-102">Parsing Strings in .NET</span></span>
<span data-ttu-id="cc39b-103">Operaci analýzy převede řetězec, který představuje základní typ rozhraní .NET do základního typu.</span><span class="sxs-lookup"><span data-stu-id="cc39b-103">A parsing operation converts a string that represents a .NET base type into that base type.</span></span> <span data-ttu-id="cc39b-104">Operaci analýzy se například používá převést řetězec na číslo s plovoucí desetinnou čárkou nebo na hodnotu data a času.</span><span class="sxs-lookup"><span data-stu-id="cc39b-104">For example, a parsing operation is used to convert a string to a floating-point number or to a date and time value.</span></span> <span data-ttu-id="cc39b-105">Metoda nejčastěji používaná k provedení analýzy operace je `Parse` metoda.</span><span class="sxs-lookup"><span data-stu-id="cc39b-105">The method most commonly used to perform a parsing operation is the `Parse` method.</span></span> <span data-ttu-id="cc39b-106">Protože analýza je reverzní operace formátování (která zahrnuje převodu základní typ jeho řetězcovou reprezentaci), řadu stejné pravidla a pravidla týkající se použití.</span><span class="sxs-lookup"><span data-stu-id="cc39b-106">Because parsing is the reverse operation of formatting (which involves converting a base type into its string representation), many of the same rules and conventions apply.</span></span> <span data-ttu-id="cc39b-107">Jenom jako formátování používá objekt, který implementuje <xref:System.IFormatProvider> poskytovat informace formátování jazykové verzi, analýza také používá objekt, který implementuje rozhraní <xref:System.IFormatProvider> rozhraní určit, jak interpretovat reprezentaci řetězce .</span><span class="sxs-lookup"><span data-stu-id="cc39b-107">Just as formatting uses an object that implements the <xref:System.IFormatProvider> interface to provide culture-sensitive formatting information, parsing also uses an object that implements the <xref:System.IFormatProvider> interface to determine how to interpret a string representation.</span></span> <span data-ttu-id="cc39b-108">Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc39b-108">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cc39b-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cc39b-109">In This Section</span></span>  
 [<span data-ttu-id="cc39b-110">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="cc39b-110">Parsing Numeric Strings</span></span>](../../../docs/standard/base-types/parsing-numeric.md)  
 <span data-ttu-id="cc39b-111">Popisuje, jak převést řetězce na číselné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="cc39b-111">Describes how to convert strings into .NET numeric types.</span></span>  
  
 [<span data-ttu-id="cc39b-112">Analýza řetězců data a času</span><span class="sxs-lookup"><span data-stu-id="cc39b-112">Parsing Date and Time Strings</span></span>](../../../docs/standard/base-types/parsing-datetime.md)  
 <span data-ttu-id="cc39b-113">Popisuje, jak převést řetězce na rozhraní .NET **data a času** typy.</span><span class="sxs-lookup"><span data-stu-id="cc39b-113">Describes how to convert strings into .NET **DateTime** types.</span></span>  
  
 [<span data-ttu-id="cc39b-114">Analýza jiných řetězců</span><span class="sxs-lookup"><span data-stu-id="cc39b-114">Parsing Other Strings</span></span>](../../../docs/standard/base-types/parsing-other.md)  
 <span data-ttu-id="cc39b-115">Popisuje, jak převést do řetězce **Char**, **Boolean**, a **výčtu** typy.</span><span class="sxs-lookup"><span data-stu-id="cc39b-115">Describes how to convert strings into **Char**, **Boolean**, and **Enum** types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cc39b-116">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cc39b-116">Related Sections</span></span>  
 [<span data-ttu-id="cc39b-117">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="cc39b-117">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="cc39b-118">Popisuje základní principy formátování jako specifikátory formátu a zprostředkovatelé formátu.</span><span class="sxs-lookup"><span data-stu-id="cc39b-118">Describes basic formatting concepts like format specifiers and format providers.</span></span>  
  
 [<span data-ttu-id="cc39b-119">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="cc39b-119">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="cc39b-120">Popisuje, jak pro převod typů.</span><span class="sxs-lookup"><span data-stu-id="cc39b-120">Describes how to convert types.</span></span>  
  
 [<span data-ttu-id="cc39b-121">Základní typy</span><span class="sxs-lookup"><span data-stu-id="cc39b-121">Base Types</span></span>](../../../docs/standard/base-types/index.md)  
 <span data-ttu-id="cc39b-122">Popisuje běžné operace, které můžete provádět na základní typy .NET.</span><span class="sxs-lookup"><span data-stu-id="cc39b-122">Describes common operations that you can perform on .NET base types.</span></span>
