---
title: Základní operace s řetězci v .NET
description: Seznamte se se základními operacemi, které můžete provádět na řetězcích.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132915"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="841c7-103">Základní operace s řetězci v .NET</span><span class="sxs-lookup"><span data-stu-id="841c7-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="841c7-104">Aplikace často reagují na uživatele tím, že vytváří zprávy na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="841c7-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="841c7-105">Nejedná se například o neobvyklou webovou lokalitu, aby reagovala na nově přihlášeného uživatele se specializovaným pozdravem, který obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="841c7-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="841c7-106">Několik metod v třídách <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> umožňuje dynamicky vytvářet vlastní řetězce pro zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="841c7-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="841c7-107">Tyto metody vám také pomůžou provést řadu základních operací s řetězci, jako je vytváření nových řetězců z polí bajtů, porovnávání hodnot řetězců a úprava stávajících řetězců.</span><span class="sxs-lookup"><span data-stu-id="841c7-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="841c7-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="841c7-108">In This Section</span></span>  
 [<span data-ttu-id="841c7-109">Vytváření nových řetězců</span><span class="sxs-lookup"><span data-stu-id="841c7-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="841c7-110">Popisuje základní způsoby, jak převést objekty do řetězců a kombinovat řetězce.</span><span class="sxs-lookup"><span data-stu-id="841c7-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="841c7-111">Ořezávání a odstraňování znaků</span><span class="sxs-lookup"><span data-stu-id="841c7-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="841c7-112">Popisuje, jak oříznout nebo odebrat znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="841c7-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="841c7-113">Doplňování řetězců</span><span class="sxs-lookup"><span data-stu-id="841c7-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="841c7-114">Popisuje, jak vložit znaky nebo prázdné mezery do řetězce.</span><span class="sxs-lookup"><span data-stu-id="841c7-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="841c7-115">Porovnávání řetězců</span><span class="sxs-lookup"><span data-stu-id="841c7-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="841c7-116">Popisuje, jak porovnat obsah dvou nebo více řetězců.</span><span class="sxs-lookup"><span data-stu-id="841c7-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="841c7-117">Změna velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="841c7-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="841c7-118">Popisuje, jak změnit velikost písmen znaků v řetězci.</span><span class="sxs-lookup"><span data-stu-id="841c7-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="841c7-119">Používání třídy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="841c7-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="841c7-120">Popisuje, jak vytvořit a upravit objekty dynamického řetězce pomocí třídy <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="841c7-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="841c7-121">Postupy: Základní manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="841c7-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="841c7-122">Ukazuje použití základních operací s řetězci.</span><span class="sxs-lookup"><span data-stu-id="841c7-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="841c7-123">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="841c7-123">Related Sections</span></span>  
 [<span data-ttu-id="841c7-124">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="841c7-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="841c7-125">Popisuje, jak převést jeden typ na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="841c7-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="841c7-126">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="841c7-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="841c7-127">Popisuje, jak formátovat řetězce pomocí specifikátorů formátu.</span><span class="sxs-lookup"><span data-stu-id="841c7-127">Describes how to format strings using format specifiers.</span></span>
