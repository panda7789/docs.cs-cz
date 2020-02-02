---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920666"
---

<span data-ttu-id="52da5-101">Při instalaci balíčku .NET Core se může zobrazit chyba podobná `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span><span class="sxs-lookup"><span data-stu-id="52da5-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="52da5-102">Obecně řečeno, tato chyba znamená, že kanál balíčku pro .NET Core se upgraduje s novějšími verzemi balíčků a že byste se měli pokusit později.</span><span class="sxs-lookup"><span data-stu-id="52da5-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="52da5-103">Během upgradu by kanál balíčku neměl být nedostupný po dobu delší než 30 minut.</span><span class="sxs-lookup"><span data-stu-id="52da5-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="52da5-104">Pokud se tato chyba průběžně zobrazuje déle než 30 minut, uveďte problém na <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="52da5-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
