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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Postupy: zobrazení obsahu globální mezipaměti sestavení

Pro zobrazení obsahu globální mezipaměti sestavení (GAC) použijte [Nástroj Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .

## <a name="view-the-assemblies-in-the-gac"></a>Zobrazit sestavení v globální mezipaměti sestavení (GAC)

Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení (GAC), otevřete [Developer Command Prompt pro sadu Visual Studio](../tools/developer-command-prompt-for-vs.md)a potom zadejte následující příkaz:

```shell
gacutil -l
```

-nebo-

```shell
gacutil /l
```

> [!NOTE]
> V dřívějších verzích .NET Framework bylo povoleno rozšíření prostředí systému Windows [Shfusion. dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) , které umožňuje zobrazit globální mezipaměť sestavení (GAC) v Průzkumníkovi souborů. Počínaje .NET Framework 4 Shfusion. dll je zastaralá.

## <a name="see-also"></a>Viz také

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
