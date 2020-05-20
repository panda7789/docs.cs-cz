---
title: Globalizace – průlomové změny
description: Obsahuje seznam nejnovějších změn v globalizaci v .NET Core.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702291"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="bb827-103">Globalizace – průlomové změny</span><span class="sxs-lookup"><span data-stu-id="bb827-103">Globalization breaking changes</span></span>

<span data-ttu-id="bb827-104">Na této stránce jsou popsány následující přerušující se změny:</span><span class="sxs-lookup"><span data-stu-id="bb827-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="bb827-105">Zásadní změna</span><span class="sxs-lookup"><span data-stu-id="bb827-105">Breaking change</span></span> | <span data-ttu-id="bb827-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="bb827-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="bb827-107">Rozhraní API globalizace používají knihovny ICU ve Windows</span><span class="sxs-lookup"><span data-stu-id="bb827-107">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="bb827-108">5.0</span><span class="sxs-lookup"><span data-stu-id="bb827-108">5.0</span></span> |
| [<span data-ttu-id="bb827-109">StringInfo a TextElementEnumerator jsou nyní kompatibilní s UAX29</span><span class="sxs-lookup"><span data-stu-id="bb827-109">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="bb827-110">5.0</span><span class="sxs-lookup"><span data-stu-id="bb827-110">5.0</span></span> |
| [<span data-ttu-id="bb827-111">Národní prostředí jazyka C se mapuje na neutrální národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="bb827-111">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="bb827-112">3.0</span><span class="sxs-lookup"><span data-stu-id="bb827-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="bb827-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="bb827-113">.NET 5.0</span></span>

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="bb827-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bb827-114">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
