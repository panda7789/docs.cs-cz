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
ms.openlocfilehash: 4142c3f12cc5a0e2277cc8dba28a281d5cf0ba55
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46578611"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Postupy: zobrazení obsahu globální mezipaměti sestavení

Použití [nástroj globální mezipaměti sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).

## <a name="view-the-assemblies-in-the-gac"></a>Zobrazení sestavení v GAC

Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení, otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:

```shell
gacutil -l
```

-nebo-

```shell
gacutil /l
```

> [!NOTE]
> V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozšíření prostředí Windows umožňovalo zobrazení mezipaměti globálního sestavení v Průzkumníku souborů. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.

## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)