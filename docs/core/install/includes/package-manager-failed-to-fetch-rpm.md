---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920745"
---

<span data-ttu-id="dcbfc-101">Při instalaci balíčku .NET Core se může zobrazit chyba podobná `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span><span class="sxs-lookup"><span data-stu-id="dcbfc-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="dcbfc-102">Obecně řečeno, tato chyba znamená, že kanál balíčku pro .NET Core se upgraduje s novějšími verzemi balíčků a že byste se měli pokusit později.</span><span class="sxs-lookup"><span data-stu-id="dcbfc-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="dcbfc-103">Během upgradu by kanál balíčku neměl být nedostupný déle než 2 hodiny.</span><span class="sxs-lookup"><span data-stu-id="dcbfc-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="dcbfc-104">Pokud se tato chyba průběžně zobrazuje déle než 2 hodiny, uveďte problém na <https://github.com/dotnet/core/issues>.</span><span class="sxs-lookup"><span data-stu-id="dcbfc-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
