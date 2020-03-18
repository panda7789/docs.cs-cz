---
title: Příklady regulárních výrazů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- regular expressions [.NET Framework], examples
- regular expressions [.NET Framework]
- strings [.NET Framework], regular expressions
ms.assetid: e9fd53f2-ed56-4b09-b2ea-e9bc9d65e6d6
ms.openlocfilehash: 788fa2a6793e14189def4c30a0baf0d4a5cf6b0a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128097"
---
# <a name="regular-expression-examples"></a><span data-ttu-id="78bf6-102">Příklady regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="78bf6-102">Regular Expression Examples</span></span>
<span data-ttu-id="78bf6-103">Tato část obsahuje příklady kódu, které ilustrují použití regulárních výrazů v běžných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="78bf6-103">This section contains code examples that illustrate the use of regular expressions in common applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78bf6-104">Obor <xref:System.Web.RegularExpressions> názvů obsahuje řadu objektů regulárních výrazů, které implementují předdefinované vzory regulárních výrazů pro analýzu řetězců z dokumentů HTML, XML a ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="78bf6-104">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="78bf6-105">Například <xref:System.Web.RegularExpressions.TagRegex> třída identifikuje počáteční značky v <xref:System.Web.RegularExpressions.CommentRegex> řetězci a třída identifikuje ASP.NET komentáře v řetězci.</span><span class="sxs-lookup"><span data-stu-id="78bf6-105">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78bf6-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="78bf6-106">In This Section</span></span>  
 [<span data-ttu-id="78bf6-107">Příklad: Vyhledávání atributů HREF</span><span class="sxs-lookup"><span data-stu-id="78bf6-107">Example: Scanning for HREFs</span></span>](../../../docs/standard/base-types/regular-expression-example-scanning-for-hrefs.md)  
 <span data-ttu-id="78bf6-108">Poskytuje příklad, který hledá vstupní řetězec a vytiskne všechny href="..." hodnoty a jejich umístění v řetězci.</span><span class="sxs-lookup"><span data-stu-id="78bf6-108">Provides an example that searches an input string and prints out all the href="…" values and their locations in the string.</span></span>  
  
 [<span data-ttu-id="78bf6-109">Příklad: Změna formátů data</span><span class="sxs-lookup"><span data-stu-id="78bf6-109">Example: Changing Date Formats</span></span>](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)  
 <span data-ttu-id="78bf6-110">Uvádí příklad, který nahrazuje data ve formuláři mm/dd/yy daty ve formuláři dd-mm-yy.</span><span class="sxs-lookup"><span data-stu-id="78bf6-110">Provides an example that replaces dates in the form mm/dd/yy with dates in the form dd-mm-yy.</span></span>  
  
 [<span data-ttu-id="78bf6-111">Postupy: Extrahování protokolu a čísla portu z adresy URL</span><span class="sxs-lookup"><span data-stu-id="78bf6-111">How to: Extract a Protocol and Port Number from a URL</span></span>](../../../docs/standard/base-types/how-to-extract-a-protocol-and-port-number-from-a-url.md)  
 <span data-ttu-id="78bf6-112">Poskytuje příklad, který extrahuje protokol a číslo portu z řetězce, který obsahuje adresu URL.</span><span class="sxs-lookup"><span data-stu-id="78bf6-112">Provides an example that extracts a protocol and port number from a string that contains a URL.</span></span> <span data-ttu-id="78bf6-113">Například "http://www.contoso.com:8080/letters/readme.html" vrátí "http:8080".</span><span class="sxs-lookup"><span data-stu-id="78bf6-113">For example, "http://www.contoso.com:8080/letters/readme.html" returns "http:8080".</span></span>  
  
 [<span data-ttu-id="78bf6-114">Postupy: Odstranění neplatných znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="78bf6-114">How to: Strip Invalid Characters from a String</span></span>](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)  
 <span data-ttu-id="78bf6-115">Poskytuje příklad, který z řetězce proužkuje neplatné nealfanumerické znaky.</span><span class="sxs-lookup"><span data-stu-id="78bf6-115">Provides an example that strips invalid non-alphanumeric characters from a string.</span></span>  
  
 [<span data-ttu-id="78bf6-116">Postup: Ověření, zda jsou řetězce v platném formátu e-mailu</span><span class="sxs-lookup"><span data-stu-id="78bf6-116">How to: Verify that Strings Are in Valid Email Format</span></span>](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)  
 <span data-ttu-id="78bf6-117">Poskytuje příklad, který ověřuje, zda je řetězec v platném formátu e-mailu.</span><span class="sxs-lookup"><span data-stu-id="78bf6-117">Provides an example that verifies that a string is in valid email format.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="78bf6-118">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="78bf6-118">Reference</span></span>  
 <xref:System.Text.RegularExpressions>  
 <span data-ttu-id="78bf6-119">Poskytuje referenční informace knihovny tříd pro obor názvů .NET **System.Text.RegularExpressions.**</span><span class="sxs-lookup"><span data-stu-id="78bf6-119">Provides class library reference information for the .NET **System.Text.RegularExpressions** namespace.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="78bf6-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="78bf6-120">Related Sections</span></span>  
 [<span data-ttu-id="78bf6-121">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="78bf6-121">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="78bf6-122">Poskytuje přehled aspektu programovacího jazyka regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="78bf6-122">Provides an overview of the programming language aspect of regular expressions.</span></span>  
  
 [<span data-ttu-id="78bf6-123">Model objektu regulárního výrazu</span><span class="sxs-lookup"><span data-stu-id="78bf6-123">The Regular Expression Object Model</span></span>](../../../docs/standard/base-types/the-regular-expression-object-model.md)  
 <span data-ttu-id="78bf6-124">Popisuje třídy regulárních `System.Text.RegularExpression` výrazů obsažené v oboru názvů a poskytuje příklady jejich použití.</span><span class="sxs-lookup"><span data-stu-id="78bf6-124">Describes the regular expression classes contained in the `System.Text.RegularExpression` namespace and provides examples of their use.</span></span>  
  
 [<span data-ttu-id="78bf6-125">Podrobnosti k chování regulárních výrazů</span><span class="sxs-lookup"><span data-stu-id="78bf6-125">Details of Regular Expression Behavior</span></span>](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)  
 <span data-ttu-id="78bf6-126">Obsahuje informace o možnostech a chování regulárních výrazů rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="78bf6-126">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>  
  
 [<span data-ttu-id="78bf6-127">Jazyk regulárních výrazů – stručná referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="78bf6-127">Regular Expression Language - Quick Reference</span></span>](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 <span data-ttu-id="78bf6-128">Poskytuje informace o sadách znaků, operátorech a konstrukcích, které lze použít pro definování regulárních výrazů.</span><span class="sxs-lookup"><span data-stu-id="78bf6-128">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>
