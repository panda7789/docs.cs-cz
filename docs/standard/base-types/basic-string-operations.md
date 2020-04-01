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
ms.openlocfilehash: 2ce1b148a2b1605b5b1283bdc3398409661f3f83
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523992"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="a6de5-103">Základní operace řetězce v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="a6de5-103">Basic string operations in .NET</span></span>

<span data-ttu-id="a6de5-104">Aplikace často reagují na uživatele vytvářením zpráv na základě vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6de5-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="a6de5-105">Například není neobvyklé, že weby reagují na nově přihlášeného uživatele se specializovaným pozdravem, který obsahuje jméno uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6de5-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="a6de5-106">Několik metod <xref:System.String?displayProperty=nameWithType> v <xref:System.Text.StringBuilder?displayProperty=nameWithType> a třídy umožňují dynamicky vytvářet vlastní řetězce pro zobrazení v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6de5-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="a6de5-107">Tyto metody také pomáhají provádět řadu základních operací řetězce, jako je vytváření nových řetězců z polí bajtů, porovnání hodnot řetězců a úprava existujících řetězců.</span><span class="sxs-lookup"><span data-stu-id="a6de5-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a6de5-108">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a6de5-108">Related sections</span></span>

<span data-ttu-id="a6de5-109">[Převod typu v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="a6de5-109">[Type Conversion in .NET](../../../docs/standard/base-types/type-conversion.md)</span></span>\
<span data-ttu-id="a6de5-110">Popisuje, jak převést jeden typ na jiný typ.</span><span class="sxs-lookup"><span data-stu-id="a6de5-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="a6de5-111">[Typy formátování](../../../docs/standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="a6de5-111">[Formatting Types](../../../docs/standard/base-types/formatting-types.md)</span></span>\
<span data-ttu-id="a6de5-112">Popisuje způsob formátování řetězců pomocí specifikátorů formátu.</span><span class="sxs-lookup"><span data-stu-id="a6de5-112">Describes how to format strings using format specifiers.</span></span>
