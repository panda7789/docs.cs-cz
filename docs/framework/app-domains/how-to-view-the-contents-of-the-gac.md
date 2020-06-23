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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Postupy: zobrazení obsahu globální mezipaměti sestavení

Použijte [nástroj globální mezipaměť sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení (GAC).

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
> V dřívějších verzích .NET Framework [Shfusion.dll](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/34149zk3(v=vs.100)) rozšíření prostředí systému Windows povoleno zobrazit globální mezipaměť sestavení (GAC) v Průzkumníkovi souborů. Počínaje .NET Framework 4 je Shfusion.dll zastaralé.

## <a name="see-also"></a>Viz také

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Gacutil.exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
