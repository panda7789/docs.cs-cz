---
title: "Základní operace s řetězci v .NET Frameworku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1ee53343a68a2c2169baefaebc68a817159d0313
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="efcba-102">Základní operace s řetězci v .NET</span><span class="sxs-lookup"><span data-stu-id="efcba-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="efcba-103">Aplikace často odpovídají uživatelům sestavením zpráv založených na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="efcba-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="efcba-104">Například neobvyklé pro weby reagovat na nově přihlášený uživatel s specializované pozdravu, která obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="efcba-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="efcba-105">Několik metod v <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy umožňují dynamicky vytvářet vlastní řetězce k zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efcba-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="efcba-106">Tyto metody také můžete provést některé základní operace s řetězci jako je vytváření nových řetězců z pole bajtů, porovnání hodnot řetězců a úpravy existujících řetězců.</span><span class="sxs-lookup"><span data-stu-id="efcba-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efcba-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="efcba-107">In This Section</span></span>  
 [<span data-ttu-id="efcba-108">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="efcba-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="efcba-109">Popisuje základní způsoby převést objekty do řetězců a seskupování řetězců.</span><span class="sxs-lookup"><span data-stu-id="efcba-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="efcba-110">Ořezávání a odstraňování znaků</span><span class="sxs-lookup"><span data-stu-id="efcba-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="efcba-111">Popisuje postup uvolnění dočasné paměti nebo odeberte znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="efcba-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="efcba-112">Doplňování řetězců</span><span class="sxs-lookup"><span data-stu-id="efcba-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="efcba-113">Popisuje, jak vložit znaky nebo prázdné mezery na řetězec.</span><span class="sxs-lookup"><span data-stu-id="efcba-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="efcba-114">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="efcba-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="efcba-115">Popisuje, jak porovnání obsahu dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="efcba-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="efcba-116">Změna velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="efcba-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="efcba-117">Popisuje, jak změnit velikost znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="efcba-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="efcba-118">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="efcba-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="efcba-119">Popisuje, jak vytvářet a upravovat objekty dynamického řetězce <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="efcba-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="efcba-120">Postupy: Základní manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="efcba-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="efcba-121">Demonstruje použití základní operace s řetězci.</span><span class="sxs-lookup"><span data-stu-id="efcba-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="efcba-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="efcba-122">Related Sections</span></span>  
 [<span data-ttu-id="efcba-123">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="efcba-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="efcba-124">Popisuje, jak převést jeden typ do jiného typu.</span><span class="sxs-lookup"><span data-stu-id="efcba-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="efcba-125">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="efcba-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="efcba-126">Popisuje postup použití specifikátorů formátu řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="efcba-126">Describes how to format strings using format specifiers.</span></span>
