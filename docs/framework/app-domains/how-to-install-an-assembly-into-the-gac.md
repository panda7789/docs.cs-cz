---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)'
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
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926516"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="30a0b-102">Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="30a0b-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="30a0b-103">Globální mezipaměť sestavení (GAC) ukládá sestavení, která sdílí několik aplikací.</span><span class="sxs-lookup"><span data-stu-id="30a0b-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="30a0b-104">Nainstalujte sestavení do [globální mezipaměti sestavení](gac.md) (GAC) pomocí jedné z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="30a0b-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="30a0b-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="30a0b-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="30a0b-106">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="30a0b-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="30a0b-107">Do globální mezipaměti sestavení (GAC) lze nainstalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="30a0b-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="30a0b-108">Informace o tom, jak vytvořit sestavení se silným názvem, naleznete [v tématu How to: Podepište sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="30a0b-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="30a0b-109">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="30a0b-109">Windows Installer</span></span>

<span data-ttu-id="30a0b-110">[Instalační služba systému Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)je instalační stroj Windows doporučeným způsobem, jak přidat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="30a0b-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="30a0b-111">Instalační služba systému Windows poskytuje počítání odkazů sestavení v globální mezipaměti sestavení (GAC) a další výhody.</span><span class="sxs-lookup"><span data-stu-id="30a0b-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="30a0b-112">Chcete-li vytvořit instalační balíček pro Instalační služba systému Windows, použijte [rozšíření sady nástrojů WIX pro sadu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="30a0b-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="30a0b-113">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="30a0b-113">Global assembly cache tool</span></span>

<span data-ttu-id="30a0b-114">K přidání sestavení do globální mezipaměti sestavení (GAC) a k zobrazení obsahu globální mezipaměti sestavení (GAC) můžete použít [Nástroj Global Assembly Cache Tool (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="30a0b-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="30a0b-115">*Gacutil. exe* je určen pouze pro účely vývoje.</span><span class="sxs-lookup"><span data-stu-id="30a0b-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="30a0b-116">Nepoužívejte jej k instalaci produkčních sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="30a0b-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="30a0b-117">Syntaxe pro použití nástroje *Gacutil. exe* pro instalaci sestavení v globální mezipaměti sestavení (GAC) je následující:</span><span class="sxs-lookup"><span data-stu-id="30a0b-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="30a0b-118">V tomto příkazu  *\<je název sestavení >* název sestavení pro instalaci do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="30a0b-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="30a0b-119">Pokud nástroj *Gacutil. exe* není v systémové cestě, použijte [Developer Command Prompt pro vs  *\<Version >* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="30a0b-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="30a0b-120">Následující příklad nainstaluje sestavení s názvem souboru *Hello. dll* do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="30a0b-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="30a0b-121">V dřívějších verzích .NET Framework rozšíření prostředí systému Windows *Shfusion. dll* umožňuje instalovat sestavení jejich přetažením do Průzkumníka souborů.</span><span class="sxs-lookup"><span data-stu-id="30a0b-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="30a0b-122">Počínaje .NET Framework 4 *Shfusion. dll* je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="30a0b-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="30a0b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30a0b-123">See also</span></span>

- [<span data-ttu-id="30a0b-124">Práce se sestaveními a globální mezipamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="30a0b-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="30a0b-125">Postupy: Odebrání sestavení z globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="30a0b-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="30a0b-126">Gacutil. exe (nástroj globální mezipaměť sestavení)</span><span class="sxs-lookup"><span data-stu-id="30a0b-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="30a0b-127">Postupy: Podepsat sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="30a0b-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
