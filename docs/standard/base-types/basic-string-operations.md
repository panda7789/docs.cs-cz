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
ms.openlocfilehash: 8c19f6bcbdf5e4829c91aee1e2fd631537ed2e0a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277749"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="01bc8-103">Základní operace s řetězci v .NET</span><span class="sxs-lookup"><span data-stu-id="01bc8-103">Basic string operations in .NET</span></span>

<span data-ttu-id="01bc8-104">Aplikace často reagují na uživatele tím, že vytváří zprávy na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="01bc8-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="01bc8-105">Nejedná se například o neobvyklé weby, aby reagovaly na nově přihlášeného uživatele se specializovaným pozdravem, který obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="01bc8-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="01bc8-106">Několik metod v <xref:System.String?displayProperty=nameWithType> <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídách a umožňuje dynamicky vytvářet vlastní řetězce pro zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="01bc8-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="01bc8-107">Tyto metody vám také pomůžou provést řadu základních operací s řetězci, jako je vytváření nových řetězců z polí bajtů, porovnávání hodnot řetězců a úprava stávajících řetězců.</span><span class="sxs-lookup"><span data-stu-id="01bc8-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="01bc8-108">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="01bc8-108">Related sections</span></span>

<span data-ttu-id="01bc8-109">[Převod typu v .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="01bc8-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="01bc8-110">Popisuje, jak převést jeden typ na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="01bc8-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="01bc8-111">[Typy formátování](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="01bc8-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="01bc8-112">Popisuje, jak formátovat řetězce pomocí specifikátorů formátu.</span><span class="sxs-lookup"><span data-stu-id="01bc8-112">Describes how to format strings using format specifiers.</span></span>
