---
title: Základní operace řetězce v rozhraní .NET
description: Další informace o základních operacích, které můžete provádět na řetězce.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132915"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="3718c-103">Základní operace řetězce v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3718c-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="3718c-104">Aplikace často reagují na uživatele vytvářením zpráv na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="3718c-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="3718c-105">Není například neobvyklé, že webové servery reagují na nově přihlášeného uživatele pomocí specializovaného pozdravu, který obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="3718c-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="3718c-106">Několik metod <xref:System.String?displayProperty=nameWithType> v <xref:System.Text.StringBuilder?displayProperty=nameWithType> a třídy umožňují dynamicky vytvářet vlastní řetězce pro zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3718c-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="3718c-107">Tyto metody také pomáhají provádět řadu základních operací řetězce, jako je vytváření nových řetězců z polí bajtů, porovnání hodnot řetězců a úprava existujících řetězců.</span><span class="sxs-lookup"><span data-stu-id="3718c-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3718c-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3718c-108">In This Section</span></span>  
 [<span data-ttu-id="3718c-109">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="3718c-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="3718c-110">Popisuje základní způsoby převodu objektů na řetězce a kombinování řetězců.</span><span class="sxs-lookup"><span data-stu-id="3718c-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="3718c-111">Ořezávání a odstraňování znaků</span><span class="sxs-lookup"><span data-stu-id="3718c-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="3718c-112">Popisuje, jak oříznout nebo odebrat znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="3718c-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="3718c-113">Doplňování řetězců</span><span class="sxs-lookup"><span data-stu-id="3718c-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="3718c-114">Popisuje, jak vložit znaky nebo prázdné mezery do řetězce.</span><span class="sxs-lookup"><span data-stu-id="3718c-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="3718c-115">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="3718c-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="3718c-116">Popisuje, jak porovnat obsah dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="3718c-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="3718c-117">Změna velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="3718c-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="3718c-118">Popisuje, jak změnit malá a velká písmena znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="3718c-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="3718c-119">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="3718c-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="3718c-120">Popisuje, jak vytvořit a upravit dynamické <xref:System.Text.StringBuilder> objekty řetězce s třídou.</span><span class="sxs-lookup"><span data-stu-id="3718c-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="3718c-121">Postupy: Základní manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="3718c-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="3718c-122">Ukazuje použití základních operací řetězce.</span><span class="sxs-lookup"><span data-stu-id="3718c-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3718c-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3718c-123">Related Sections</span></span>  
 [<span data-ttu-id="3718c-124">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3718c-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="3718c-125">Popisuje, jak převést jeden typ na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="3718c-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="3718c-126">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="3718c-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="3718c-127">Popisuje způsob formátování řetězců pomocí specifikátorů formátu.</span><span class="sxs-lookup"><span data-stu-id="3718c-127">Describes how to format strings using format specifiers.</span></span>
