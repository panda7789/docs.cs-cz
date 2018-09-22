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
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="0fe82-102">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="0fe82-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="0fe82-103">Existují dva způsoby instalace sestavení se silným názvem do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0fe82-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0fe82-104">Do mezipaměti GAC lze instalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0fe82-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="0fe82-105">Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [postupy: podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="0fe82-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="0fe82-106">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="0fe82-106">Windows Installer</span></span>

<span data-ttu-id="0fe82-107">[Instalační program Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), instalace modulu Windows je doporučený způsob přidávání sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fe82-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="0fe82-108">Instalační služby systému Windows poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.</span><span class="sxs-lookup"><span data-stu-id="0fe82-108">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="0fe82-109">Můžete použít [sadu nástrojů WiX Toolset rozšíření pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) vytvoření instalačního balíčku pro Instalační služby systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0fe82-109">You can use the [WiX Toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) to create an installer package for Windows Installer.</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="0fe82-110">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="0fe82-110">Global assembly cache tool</span></span>

<span data-ttu-id="0fe82-111">Můžete použít [nástroj Global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidání sestavení se silným názvem do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fe82-111">You can use the [Global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0fe82-112">Nástroj Gacutil.exe slouží pouze pro účely vývoje a neměl by být používán k instalaci produkčních sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fe82-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="0fe82-113">Syntaxe pro gacutil vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="0fe82-113">The syntax for gacutil is as follows:</span></span>

```shell
gacutil -i <assembly name>
```

<span data-ttu-id="0fe82-114">V tomto příkazu *název sestavení* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fe82-114">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="0fe82-115">Následující příklad nainstaluje sestavení s názvem souboru `hello.dll` do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fe82-115">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>

```shell
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="0fe82-116">V dřívějších verzích rozhraní .NET Framework rozšíření prostředí Windows Shfusion.dll umožňovala instalaci sestavení přetažením **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="0fe82-116">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in **File Explorer**.</span></span> <span data-ttu-id="0fe82-117">Od verze rozhraní .NET Framework 4, je rozšíření Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="0fe82-117">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fe82-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fe82-118">See also</span></span>

- [<span data-ttu-id="0fe82-119">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="0fe82-119">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="0fe82-120">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="0fe82-120">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="0fe82-121">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="0fe82-121">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="0fe82-122">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="0fe82-122">How to: Sign an Assembly with a Strong Name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)