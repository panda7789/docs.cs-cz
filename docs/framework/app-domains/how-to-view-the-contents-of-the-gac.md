---
title: 'Postupy: Zobrazení obsahu globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
ms.openlocfilehash: b5d8b31e7eb23789878da620f3a4517056a1ee3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119835"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="6a391-102">Postupy: zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="6a391-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="6a391-103">Pro zobrazení obsahu globální mezipaměti sestavení (GAC) použijte [Nástroj Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="6a391-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="6a391-104">Zobrazit sestavení v globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="6a391-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="6a391-105">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení (GAC), otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="6a391-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="6a391-106">-nebo-</span><span class="sxs-lookup"><span data-stu-id="6a391-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="6a391-107">V dřívějších verzích .NET Framework bylo povoleno rozšíření prostředí systému Windows [Shfusion. dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) , které umožňuje zobrazit globální mezipaměť sestavení (GAC) v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="6a391-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="6a391-108">Počínaje .NET Framework 4 Shfusion. dll je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="6a391-108">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a391-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a391-109">See also</span></span>

- [<span data-ttu-id="6a391-110">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="6a391-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="6a391-111">Gacutil. exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="6a391-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
