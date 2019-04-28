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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0375c835dea8984db34d3d1e24b2876fb9af8337
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705594"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="385fb-102">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="385fb-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="385fb-103">Použití [nástroj globální mezipaměti sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="385fb-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="385fb-104">Zobrazení sestavení v GAC</span><span class="sxs-lookup"><span data-stu-id="385fb-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="385fb-105">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení, otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="385fb-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="385fb-106">-nebo-</span><span class="sxs-lookup"><span data-stu-id="385fb-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="385fb-107">V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozšíření prostředí Windows umožňovalo zobrazení mezipaměti globálního sestavení v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="385fb-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="385fb-108">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="385fb-108">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="385fb-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="385fb-109">See also</span></span>

- [<span data-ttu-id="385fb-110">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="385fb-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="385fb-111">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="385fb-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)