---
ms.openlocfilehash: 15418d1ac3ade6a0fa35ca61a02134e20af1baea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602976"
---

<span data-ttu-id="96280-101">Při instalaci balíčku .NET Core se může zobrazit chyba podobná této `Failed to fetch ... File has unexpected size ... Mirror sync in progress?` .</span><span class="sxs-lookup"><span data-stu-id="96280-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="96280-102">Tato chyba by mohla znamenat, že informační kanál balíčku pro .NET Core se upgraduje s novějšími verzemi balíčků a že byste se měli pokusit později.</span><span class="sxs-lookup"><span data-stu-id="96280-102">This error could mean that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="96280-103">Během upgradu by kanál balíčku neměl být nedostupný po dobu delší než 30 minut.</span><span class="sxs-lookup"><span data-stu-id="96280-103">During an upgrade, the package feed shouldn't be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="96280-104">Pokud se tato chyba zobrazuje stále déle než 30 minut, uveďte problém na adrese <https://github.com/dotnet/core/issues> .</span><span class="sxs-lookup"><span data-stu-id="96280-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
