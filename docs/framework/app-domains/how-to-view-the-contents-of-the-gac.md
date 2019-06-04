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
ms.openlocfilehash: c319c5f7c9bb808b2ce7ee10178722287e456339
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486426"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="62e39-102">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="62e39-102">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="62e39-103">Použití [nástroj globální mezipaměti sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="62e39-103">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="62e39-104">Zobrazení sestavení v GAC</span><span class="sxs-lookup"><span data-stu-id="62e39-104">View the assemblies in the GAC</span></span>

<span data-ttu-id="62e39-105">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení, otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="62e39-105">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="62e39-106">-nebo-</span><span class="sxs-lookup"><span data-stu-id="62e39-106">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="62e39-107">V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozšíření prostředí Windows umožňovalo zobrazení mezipaměti globálního sestavení v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="62e39-107">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="62e39-108">Od verze rozhraní .NET Framework 4, je rozšíření Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="62e39-108">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="62e39-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62e39-109">See also</span></span>

- [<span data-ttu-id="62e39-110">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="62e39-110">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="62e39-111">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="62e39-111">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
