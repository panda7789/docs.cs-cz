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
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155560"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="0ec6f-102">Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="0ec6f-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="0ec6f-103">Globální mezipaměť sestavení (GAC) ukládá sestavení, která sdílí několik aplikací.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="0ec6f-104">Nainstalujte sestavení do [globální mezipaměti sestavení](gac.md) (GAC) pomocí jedné z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="0ec6f-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="0ec6f-105">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="0ec6f-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="0ec6f-106">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="0ec6f-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="0ec6f-107">Do globální mezipaměti sestavení (GAC) lze nainstalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="0ec6f-108">Informace o tom, jak vytvořit sestavení se silným názvem, naleznete v tématu [How to: Sign a Assembly se silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="0ec6f-109">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="0ec6f-109">Windows Installer</span></span>

<span data-ttu-id="0ec6f-110">[Instalační služba systému Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)je instalační stroj Windows doporučeným způsobem, jak přidat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="0ec6f-111">Instalační služba systému Windows poskytuje počítání odkazů sestavení v globální mezipaměti sestavení (GAC) a další výhody.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="0ec6f-112">Chcete-li vytvořit instalační balíček pro Instalační služba systému Windows, použijte [rozšíření sady nástrojů WIX pro sadu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="0ec6f-113">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="0ec6f-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="0ec6f-114">K přidání sestavení do globální mezipaměti sestavení (GAC) a k zobrazení obsahu globální mezipaměti sestavení (GAC) můžete použít [Nástroj Global Assembly Cache (Gacutil. exe) .NET](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="0ec6f-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0ec6f-115">*Gacutil. exe* je určen pouze pro účely vývoje.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="0ec6f-116">Nepoužívejte jej k instalaci produkčních sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="0ec6f-117">Syntaxe pro použití nástroje *Gacutil. exe* pro instalaci sestavení v globální mezipaměti sestavení (GAC) je následující:</span><span class="sxs-lookup"><span data-stu-id="0ec6f-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="0ec6f-118">V tomto příkazu je \* \<název sestavení>\* název sestavení pro instalaci do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="0ec6f-119">Pokud nástroj *Gacutil. exe* není v systémové cestě, použijte [příkazový řádek pro vývojáře pro vs \* \<Version>\* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="0ec6f-120">Následující příklad nainstaluje sestavení s názvem souboru *Hello. dll* do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="0ec6f-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="0ec6f-121">V dřívějších verzích .NET Framework rozšíření prostředí systému Windows *Shfusion. dll* umožňuje instalovat sestavení jejich přetažením do Průzkumníka souborů.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="0ec6f-122">Počínaje .NET Framework 4 *Shfusion. dll* je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0ec6f-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ec6f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ec6f-123">See also</span></span>

- [<span data-ttu-id="0ec6f-124">Práce se sestaveními a globální mezipamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="0ec6f-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="0ec6f-125">Postupy: odebrání sestavení z globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="0ec6f-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="0ec6f-126">Gacutil. exe (nástroj globální mezipaměť sestavení)</span><span class="sxs-lookup"><span data-stu-id="0ec6f-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="0ec6f-127">Postupy: podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="0ec6f-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
