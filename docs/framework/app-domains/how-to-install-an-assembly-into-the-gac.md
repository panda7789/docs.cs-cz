---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení'
ms.date: 02/05/2019
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
ms.openlocfilehash: 233a7803cb59f9bfeac15d293dc3fb5a0db449c9
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903765"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>Postupy: Instalace sestavení do globální mezipaměti sestavení

Globální mezipaměti sestavení (GAC) ukládá sestavení, které sdílí několik aplikací. Instalace sestavení do [globální mezipaměti sestavení](gac.md) s jedním z následujících součástí: 
- [Windows Installer](#windows-installer)
- [Nástroj globální mezipaměti sestavení](#global-assembly-cache-tool)

> [!IMPORTANT]
> Nainstalujte pouze sestavení se silným názvem do mezipaměti GAC. Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [jak: Podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md).

## <a name="windows-installer"></a>Instalační služba systému Windows

[Instalační program Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), instalace modulu Windows je doporučený způsob přidávání sestavení do globální mezipaměti sestavení. Instalační služby systému Windows poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody. Vytvoření instalačního balíčku pro Instalační služby systému Windows, použijte [WiX toolset rozšíření pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

## <a name="global-assembly-cache-tool"></a>Nástroj globální mezipaměti sestavení

Můžete použít [nástroj globální mezipaměti sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidávání sestavení do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.

   > [!NOTE]
   > *Gacutil.exe* je jenom pro účely vývoje. Nepoužívejte ho k instalaci produkčních sestavení do globální mezipaměti sestavení.

Syntaxe pro používání *gacutil.exe* instalace sestavení do GAC vypadá takto:

```console
gacutil -i <assembly name>
```

V tomto příkazu  *\<název sestavení >* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.

Pokud *gacutil.exe* není v systémové cestě, použijte [Developer Command Prompt for VS  *\<verze >*](../tools/developer-command-prompt-for-vs.md).

Následující příklad nainstaluje sestavení s názvem souboru *hello.dll* do globální mezipaměti sestavení.

```console
gacutil -i hello.dll
```

> [!NOTE]
> V dřívějších verzích rozhraní .NET Framework *Shfusion.dll* rozšíření prostředí Windows umožňují instalaci sestavení přetažením do Průzkumníka souborů. Od verze rozhraní .NET Framework 4, *Shfusion.dll* je zastaralý.

## <a name="see-also"></a>Viz také:

- [Práce se sestaveními a globální mezipaměti sestavení](working-with-assemblies-and-the-gac.md)
- [Postupy: Odebrání sestavení z globální mezipaměti sestavení](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../tools/gacutil-exe-gac-tool.md)
- [Postupy: Podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md)
