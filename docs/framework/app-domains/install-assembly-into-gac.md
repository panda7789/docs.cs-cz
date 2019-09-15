---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)'
ms.date: 08/20/2019
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
ms.openlocfilehash: de5ae03ab885c4368e39b6339b5a14d1082e6df5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972933"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)

Globální mezipaměť sestavení (GAC) ukládá sestavení, která sdílí několik aplikací. Nainstalujte sestavení do [globální mezipaměti sestavení](gac.md) (GAC) pomocí jedné z následujících součástí: 

- [Windows Installer](#windows-installer)
- [Nástroj globální mezipaměti sestavení](#global-assembly-cache-tool)

> [!IMPORTANT]
> Do globální mezipaměti sestavení (GAC) lze nainstalovat pouze sestavení se silným názvem. Informace o tom, jak vytvořit sestavení se silným názvem, naleznete [v tématu How to: Podepište sestavení silným názvem](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Instalační služba systému Windows

[Instalační služba systému Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)je instalační stroj Windows doporučeným způsobem, jak přidat sestavení do globální mezipaměti sestavení (GAC). Instalační služba systému Windows poskytuje počítání odkazů sestavení v globální mezipaměti sestavení (GAC) a další výhody. Chcete-li vytvořit instalační balíček pro Instalační služba systému Windows, použijte [rozšíření sady nástrojů WIX pro sadu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>nástroj globální mezipaměti sestavení

K přidání sestavení do globální mezipaměti sestavení (GAC) a k zobrazení obsahu globální mezipaměti sestavení (GAC) můžete použít [Nástroj Global Assembly Cache (Gacutil. exe) .NET](../tools/gacutil-exe-gac-tool.md) .

   > [!NOTE]
   > *Gacutil. exe* je určen pouze pro účely vývoje. Nepoužívejte jej k instalaci produkčních sestavení do globální mezipaměti sestavení (GAC).

Syntaxe pro použití nástroje *Gacutil. exe* pro instalaci sestavení v globální mezipaměti sestavení (GAC) je následující:

```cmd
gacutil -i <assembly name>
```

V tomto příkazu  *\<je název sestavení >* název sestavení pro instalaci do globální mezipaměti sestavení (GAC).

Pokud nástroj *Gacutil. exe* není v systémové cestě, použijte [příkazový řádek pro vývojáře pro vs  *\<Version >* ](../tools/developer-command-prompt-for-vs.md).

Následující příklad nainstaluje sestavení s názvem souboru *Hello. dll* do globální mezipaměti sestavení (GAC).

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> V dřívějších verzích .NET Framework rozšíření prostředí systému Windows *Shfusion. dll* umožňuje instalovat sestavení jejich přetažením do Průzkumníka souborů. Počínaje .NET Framework 4 *Shfusion. dll* je zastaralá.

## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a globální mezipamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Postupy: Odebrání sestavení z globální mezipaměti sestavení (GAC)](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil. exe (nástroj globální mezipaměť sestavení)](../tools/gacutil-exe-gac-tool.md)
- [Postupy: Podepsat sestavení silným názvem](../../standard/assembly/sign-strong-name.md)
