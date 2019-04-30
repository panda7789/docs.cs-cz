---
title: Základní operace s řetězci v .NET
description: Přečtěte si o základních operací, které můžete provádět na řetězce.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.custom: seadec18
ms.openlocfilehash: 8621e79ad6e305f3859dc269965ecd216081f695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936809"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="7e137-103">Základní operace s řetězci v .NET</span><span class="sxs-lookup"><span data-stu-id="7e137-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="7e137-104">Aplikace často reagovat na uživatele pomocí zprávy založené na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="7e137-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="7e137-105">Není například neobvyklé webových stránek a reagovat na nově přihlášeného uživatele s specializované pozdrav, který obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="7e137-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="7e137-106">Několik metod v <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy umožňují dynamicky vytvářet vlastní řetězce k zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7e137-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="7e137-107">Tyto metody také umožňují provádět základní operace s řetězci jako je vytváření nových řetězců z pole bajtů, porovnání hodnot řetězců a úpravy existujících řetězců.</span><span class="sxs-lookup"><span data-stu-id="7e137-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e137-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7e137-108">In This Section</span></span>  
 [<span data-ttu-id="7e137-109">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="7e137-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="7e137-110">Popisuje základní způsoby k převedení objektů na řetězce a kombinování řetězců.</span><span class="sxs-lookup"><span data-stu-id="7e137-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="7e137-111">Ořezávání a odstraňování znaků</span><span class="sxs-lookup"><span data-stu-id="7e137-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="7e137-112">Popisuje, jak trim nebo odeberte znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="7e137-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="7e137-113">Doplňování řetězců</span><span class="sxs-lookup"><span data-stu-id="7e137-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="7e137-114">Popisuje, jak vkládat znaky nebo prázdné mezery do řetězce.</span><span class="sxs-lookup"><span data-stu-id="7e137-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="7e137-115">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="7e137-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="7e137-116">Popisuje, jak porovnání obsahu dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="7e137-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="7e137-117">Změna velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="7e137-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="7e137-118">Popisuje, jak změnit velikost písmen znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="7e137-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="7e137-119">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="7e137-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="7e137-120">Popisuje, jak vytvářet a upravovat objekty dynamického řetězce <xref:System.Text.StringBuilder> třídy.</span><span class="sxs-lookup"><span data-stu-id="7e137-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="7e137-121">Postupy: Manipulace s řetězci základní</span><span class="sxs-lookup"><span data-stu-id="7e137-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="7e137-122">Ukazuje použití základní operace s řetězci.</span><span class="sxs-lookup"><span data-stu-id="7e137-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7e137-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7e137-123">Related Sections</span></span>  
 [<span data-ttu-id="7e137-124">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="7e137-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="7e137-125">Popisuje, jak převést jednoho typu na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="7e137-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="7e137-126">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="7e137-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="7e137-127">Popisuje, jak pomocí specifikátorů formátu řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="7e137-127">Describes how to format strings using format specifiers.</span></span>
