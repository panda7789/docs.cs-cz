---
ms.openlocfilehash: 96f3ef0160144322f77413995c842b745bb5bb1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920745"
---

<span data-ttu-id="887ea-101">Při instalaci balíčku .NET Core se může `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`zobrazit chyba podobná .</span><span class="sxs-lookup"><span data-stu-id="887ea-101">While installing the .NET Core package, you may see an error similar to `signature verification failed for file 'repomd.xml' from repository 'packages-microsoft-com-prod'`.</span></span> <span data-ttu-id="887ea-102">Obecně řečeno, tato chyba znamená, že zdroj balíčku pro .NET Core je upgradován novějšími verzemi balíčků a že byste to měli zkusit znovu později.</span><span class="sxs-lookup"><span data-stu-id="887ea-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="887ea-103">Během upgradu by neměl být zdroj balíčku k dispozici déle než 2 hodiny.</span><span class="sxs-lookup"><span data-stu-id="887ea-103">During an upgrade, the package feed should not be unavailable for more than 2 hours.</span></span> <span data-ttu-id="887ea-104">Pokud se tato chyba zobrazuje nepřetržitě déle než 2 <https://github.com/dotnet/core/issues>hodiny, podejte problém na adrese .</span><span class="sxs-lookup"><span data-stu-id="887ea-104">If you continually receive this error for more than 2 hours, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
