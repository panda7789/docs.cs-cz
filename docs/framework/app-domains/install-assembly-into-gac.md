---
title: 'Postup: Instalace sestavení do globální mezipaměti sestavení'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155560"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postup: Instalace sestavení do globální mezipaměti sestavení

Globální mezipaměti sestavení (GAC) ukládá sestavení, které sdílejí několik aplikací. Nainstalujte sestavení do [globální mezipaměti sestavení](gac.md) s jednou z následujících součástí:

- [Instalační služba systému Windows](#windows-installer)
- [Nástroj globální mezipaměti sestavení](#global-assembly-cache-tool)

> [!IMPORTANT]
> Do globální mezipaměti sestavení můžete nainstalovat pouze sestavení se silným názvem. Informace o tom, jak vytvořit sestavení se silným názvem, naleznete v [tématu How to: Sign a assembly with a strong name](../../standard/assembly/sign-strong-name.md).

## <a name="windows-installer"></a>Instalační služba systému Windows

[Instalační služba systému Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), instalační modul systému Windows, je doporučenýzpůsob přidání sestavení do globální mezipaměti sestavení. Instalační služba systému Windows poskytuje počítání odkazů sestavení v globální mezipaměti sestavení a další výhody. Chcete-li vytvořit instalační balíček pro Instalační službu systému Windows, použijte [rozšíření sady nástrojů WiX pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Nástroj globální mezipaměti sestavení

Nástroj [.NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) můžete použít k přidání sestavení do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.

   > [!NOTE]
   > *Gacutil.exe* je pouze pro rozvojové účely. Nepoužívejte jej k instalaci produkčních sestavení do globální mezipaměti sestavení.

Syntaxe pro použití *gacutil.exe* k instalaci sestavení v GAC je následující:

```cmd
gacutil -i <assembly name>
```

V tomto * \<* příkazu název sestavení>je název sestavení k instalaci do globální mezipaměti sestavení.

Pokud *program gacutil.exe* není v systémové cestě, použijte [příkazový řádek Vývojář pro verzi VS * \<>* ](../tools/developer-command-prompt-for-vs.md).

Následující příklad nainstaluje sestavení s názvem souboru *hello.dll* do globální mezipaměti sestavení.

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> V dřívějších verzích rozhraní .NET Framework umožňuje rozšíření prostředí Systému Windows *Shfusion.dll* instalovat sestavení jejich přetažením do Průzkumníka souborů. Počínaje rozhraním .NET Framework 4 je *soubor Shfusion.dll* zastaralý.

## <a name="see-also"></a>Viz také

- [Práce se sestavami a globální mezipamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Postup: Odebrání sestavení z globální mezipaměti sestavení](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)
- [Postup: Podepsání sestavení se silným názvem](../../standard/assembly/sign-strong-name.md)
