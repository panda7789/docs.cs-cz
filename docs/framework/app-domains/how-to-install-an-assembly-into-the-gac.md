---
title: Instalace sestavení do GAC
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584578"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postupy: Instalace sestavení do globální mezipaměti sestavení

Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC).

> [!IMPORTANT]
> Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem. Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Instalační služba systému Windows

[Instalační program Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), instalace modulu Windows je doporučený způsob přidávání sestavení do globální mezipaměti sestavení. Instalační služby systému Windows poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody. Můžete použít [sadu nástrojů WiX Toolset rozšíření pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) vytvoření instalačního balíčku pro Instalační služby systému Windows.

## <a name="global-assembly-cache-tool"></a>Nástroj globální mezipaměti sestavení

Můžete použít [nástroj Global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.

   > [!NOTE]
   > Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.

Syntaxe pro gacutil vypadá takto:

```shell
gacutil -i <assembly name>
```

V tomto příkazu *název sestavení* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.

Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.

```shell
gacutil -i hello.dll
```

> [!NOTE]
> V dřívějších verzích rozhraní .NET Framework rozšíření prostředí Windows Shfusion.dll umožňovala instalaci sestavení přetažením **Průzkumníka souborů**. Od verze rozhraní .NET Framework 4, je rozšíření Shfusion.dll zastaralé.

## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Postupy: Odebrání sestavení z globální mezipaměti sestavení](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)
- [Postupy: Podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md)