---
title: 'Postupy: Zobrazení obsahu globální mezipaměti sestavení'
description: Zjistěte, jak zobrazit obsah globální mezipaměti sestavení v rozhraní .NET pomocí nástroje globální mezipaměť sestavení (GAC) (gacutil.exe).
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
ms.openlocfilehash: 4d775efc073f3aad745eff7a7707efdec06172c2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104691"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="1b0be-103">Postupy: zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="1b0be-103">How to: View the contents of the global assembly cache</span></span>

<span data-ttu-id="1b0be-104">Použijte [nástroj globální mezipaměť sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="1b0be-104">Use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache (GAC).</span></span>

## <a name="view-the-assemblies-in-the-gac"></a><span data-ttu-id="1b0be-105">Zobrazit sestavení v globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="1b0be-105">View the assemblies in the GAC</span></span>

<span data-ttu-id="1b0be-106">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení (GAC), otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1b0be-106">To view a list of the assemblies in the global assembly cache, open [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md), and then enter the following command:</span></span>

```shell
gacutil -l
```

<span data-ttu-id="1b0be-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="1b0be-107">-or-</span></span>

```shell
gacutil /l
```

> [!NOTE]
> <span data-ttu-id="1b0be-108">V dřívějších verzích .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozšíření prostředí systému Windows povoleno zobrazit globální mezipaměť sestavení (GAC) v Průzkumníkovi souborů.</span><span class="sxs-lookup"><span data-stu-id="1b0be-108">In earlier versions of the .NET Framework, the [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="1b0be-109">Počínaje .NET Framework 4 je Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="1b0be-109">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="1b0be-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b0be-110">See also</span></span>

- [<span data-ttu-id="1b0be-111">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="1b0be-111">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="1b0be-112">Gacutil.exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="1b0be-112">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
