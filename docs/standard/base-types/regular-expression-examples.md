---
title: Příklady regulárních výrazů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee4d884a0efbeb6e57ed727396bf3bcb39979774
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811563"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="e4b77-102">Příklady regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="e4b77-102">Regular Expression Examples</span></span>
<span data-ttu-id="e4b77-103">Tato část obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžných aplikací.</span><span class="sxs-lookup"><span data-stu-id="e4b77-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4b77-104"><xref:System.Web.RegularExpressions> Obor názvů obsahuje mnoho objekty regulárních výrazů, které implementují předdefinované vzory regulárních výrazů pro analýzu řetězce z dokumentů HTML, XML a ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e4b77-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="e4b77-105">Například <xref:System.Web.RegularExpressions.TagRegex> třídy identifikuje počáteční značky v řetězci a <xref:System.Web.RegularExpressions.CommentRegex> třídy identifikuje komentáře technologie ASP.NET v řetězci.</span><span class="sxs-lookup"><span data-stu-id="e4b77-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4b77-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e4b77-106">In This Section</span></span>  
 [<span data-ttu-id="e4b77-107">Příklad: Vyhledávání atributů href</span><span class="sxs-lookup"><span data-stu-id="e4b77-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="e4b77-108">Poskytuje příklad, který prohledá vstupního řetězce a vytiskne všechny href = "..." hodnoty a jejich umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="e4b77-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="e4b77-109">Příklad: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="e4b77-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="e4b77-110">Poskytuje příklad, který nahradí data ve formě mm/dd/rr s daty ve formátu dd-mm rr.</span><span class="sxs-lookup"><span data-stu-id="e4b77-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="e4b77-111">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="e4b77-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="e4b77-112">Poskytuje příklad, který extrahuje protokol a číslo portu z řetězce, který obsahuje adresu URL.</span><span class="sxs-lookup"><span data-stu-id="e4b77-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="e4b77-113">Například "http://www.contoso.com:8080/letters/readme.html" vrátí "http:8080".</span><span class="sxs-lookup"><span data-stu-id="e4b77-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="e4b77-114">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="e4b77-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="e4b77-115">Poskytuje příklad, který odstraní neplatný jiných než alfanumerických znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="e4b77-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="e4b77-116">Postupy: Ověřte, zda jsou řetězce ve formátu platné e-mailu</span><span class="sxs-lookup"><span data-stu-id="e4b77-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="e4b77-117">Poskytuje příklad, který ověřuje, že je řetězec ve formátu platné e-mailu.</span><span class="sxs-lookup"><span data-stu-id="e4b77-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e4b77-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e4b77-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="e4b77-119">Poskytuje informace o odkaz na knihovnu tříd pro .NET **System.Text.RegularExpressions** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4b77-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4b77-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e4b77-120">Related Sections</span></span>  
 [<span data-ttu-id="e4b77-121">Regulárních výrazů .NET</span><span class="sxs-lookup"><span data-stu-id="e4b77-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="e4b77-122">Poskytuje přehled o programovací jazyk aspekt regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="e4b77-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="e4b77-123">Model objektu regulárního výrazu</span><span class="sxs-lookup"><span data-stu-id="e4b77-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="e4b77-124">Popisuje třídy regulárních výrazů, které jsou součástí `System.Text.RegularExpression` obor názvů a poskytuje příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="e4b77-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="e4b77-125">Podrobnosti k chování regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="e4b77-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="e4b77-126">Poskytuje informace o možnostech a chování regulárních výrazů .NET.</span><span class="sxs-lookup"><span data-stu-id="e4b77-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="e4b77-127">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="e4b77-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="e4b77-128">Poskytuje informace o sadách znaků, operátorech a konstrukcích, které lze použít pro definování regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="e4b77-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
