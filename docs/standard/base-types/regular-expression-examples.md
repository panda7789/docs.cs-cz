---
title: "Příklady regulárních výrazů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d7fa8fe2bade9f20f71f846c717d79d6b6ffb36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="regular-expression-examples"></a><span data-ttu-id="d2dd8-102">Příklady regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="d2dd8-102">Regular Expression Examples</span></span>
<span data-ttu-id="d2dd8-103">Tato část obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžné aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2dd8-104"><xref:System.Web.RegularExpressions> Obor názvů obsahuje počet objektů regulárních výrazů, které implementují předdefinované vzory regulárních výrazů k analýze řetězců z dokumentů HTML, XML a technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="d2dd8-105">Například <xref:System.Web.RegularExpressions.TagRegex> třída identifikuje počáteční značky v řetězci a <xref:System.Web.RegularExpressions.CommentRegex> třída identifikuje komentáře technologie ASP.NET v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d2dd8-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d2dd8-106">In This Section</span></span>  
 [<span data-ttu-id="d2dd8-107">Příklad: Vyhledávání atributů href</span><span class="sxs-lookup"><span data-stu-id="d2dd8-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="d2dd8-108">Poskytuje příklad, který prohledá vstupní řetězec a vytiskne všechny href = "..." a jejich umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="d2dd8-109">Příklad: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="d2dd8-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="d2dd8-110">Poskytuje příklad, který nahradí data ve formátu mm/dd/rr s daty ve formátu dd-mm rr.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="d2dd8-111">Postupy: extrahování protokolu a číslo portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="d2dd8-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="d2dd8-112">Poskytuje příklad, který extrahuje protokol a číslo portu z řetězce, který obsahuje adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="d2dd8-113">Například "http://www.contoso.com: 8080/letters/readme.html" vrátí "http:8080".</span><span class="sxs-lookup"><span data-stu-id="d2dd8-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="d2dd8-114">Postupy: odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="d2dd8-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="d2dd8-115">Poskytuje příklad, který odstraní neplatný jiných než alfanumerických znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="d2dd8-116">Postupy: Ověřte, zda řetězce jsou ve formátu platné e-mailu</span><span class="sxs-lookup"><span data-stu-id="d2dd8-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="d2dd8-117">Poskytuje příklad, který můžete použít k ověření, že je řetězec ve formátu platné e-mailu.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-117">Provides an example that you can use to verify that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d2dd8-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d2dd8-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="d2dd8-119">Poskytuje třídy knihovny referenční informace pro .NET **System.Text.RegularExpressions** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d2dd8-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d2dd8-120">Related Sections</span></span>  
 [<span data-ttu-id="d2dd8-121">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d2dd8-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="d2dd8-122">Poskytuje přehled programovací jazyk aspektů regulární výrazy.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="d2dd8-123">Model objektu regulárního výrazu</span><span class="sxs-lookup"><span data-stu-id="d2dd8-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="d2dd8-124">Popisuje třídy regulárních výrazů, které jsou součástí `System.Text.RegularExpression` obor názvů a poskytuje příkladů jeho použití.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="d2dd8-125">Podrobnosti k chování regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="d2dd8-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="d2dd8-126">Poskytuje informace o možnostech a chování regulárních výrazech .NET.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="d2dd8-127">Jazyk regulárních výrazů – Stručná referenční příručka</span><span class="sxs-lookup"><span data-stu-id="d2dd8-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="d2dd8-128">Poskytuje informace o sadách znaků, operátorech a konstrukcích, které lze použít pro definování regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="d2dd8-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
