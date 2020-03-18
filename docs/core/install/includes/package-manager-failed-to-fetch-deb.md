---
ms.openlocfilehash: 98ec28fc1f91512a61f64a36f7749379e864fea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920666"
---

<span data-ttu-id="179cb-101">Při instalaci balíčku .NET Core se může `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`zobrazit chyba podobná .</span><span class="sxs-lookup"><span data-stu-id="179cb-101">While installing the .NET Core package, you may see an error similar to `Failed to fetch ... File has unexpected size ... Mirror sync in progress?`.</span></span> <span data-ttu-id="179cb-102">Obecně řečeno, tato chyba znamená, že zdroj balíčku pro .NET Core je upgradován novějšími verzemi balíčků a že byste to měli zkusit znovu později.</span><span class="sxs-lookup"><span data-stu-id="179cb-102">Generally speaking, this error means that the package feed for .NET Core is being upgraded with newer package versions, and that you should try again later.</span></span> <span data-ttu-id="179cb-103">Během upgradu by neměl být informační kanál balíčku k dispozici déle než 30 minut.</span><span class="sxs-lookup"><span data-stu-id="179cb-103">During an upgrade, the package feed should not be unavailable for more than 30 minutes.</span></span> <span data-ttu-id="179cb-104">Pokud se tato chyba zobrazuje nepřetržitě déle než 30 <https://github.com/dotnet/core/issues>minut, podejte problém na adrese .</span><span class="sxs-lookup"><span data-stu-id="179cb-104">If you continually receive this error for more than 30 minutes, please file an issue at <https://github.com/dotnet/core/issues>.</span></span>
