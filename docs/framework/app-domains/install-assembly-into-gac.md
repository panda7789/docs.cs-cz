---
title: 'Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)'
description: Nainstalujte sestavení do globální mezipaměti sestavení (GAC) v rozhraní .NET, aby jej bylo možné sdílet mnoha aplikacemi. Použijte Instalační služba systému Windows nebo nástroj GAC.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104673"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="96bb6-104">Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="96bb6-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="96bb6-105">Globální mezipaměť sestavení (GAC) ukládá sestavení, která sdílí několik aplikací.</span><span class="sxs-lookup"><span data-stu-id="96bb6-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="96bb6-106">Nainstalujte sestavení do [globální mezipaměti sestavení](gac.md) (GAC) pomocí jedné z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="96bb6-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="96bb6-107">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="96bb6-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="96bb6-108">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="96bb6-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="96bb6-109">Do globální mezipaměti sestavení (GAC) lze nainstalovat pouze sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="96bb6-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="96bb6-110">Informace o tom, jak vytvořit sestavení se silným názvem, naleznete v tématu [How to: Sign a Assembly se silným názvem](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="96bb6-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="96bb6-111">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="96bb6-111">Windows Installer</span></span>

<span data-ttu-id="96bb6-112">[Instalační služba systému Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)je instalační stroj Windows doporučeným způsobem, jak přidat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="96bb6-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="96bb6-113">Instalační služba systému Windows poskytuje počítání odkazů sestavení v globální mezipaměti sestavení (GAC) a další výhody.</span><span class="sxs-lookup"><span data-stu-id="96bb6-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="96bb6-114">Chcete-li vytvořit instalační balíček pro Instalační služba systému Windows, použijte [rozšíření sady nástrojů WIX pro sadu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="96bb6-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="96bb6-115">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="96bb6-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="96bb6-116">K přidání sestavení do globální mezipaměti sestavení (GAC) a k zobrazení obsahu globální mezipaměti sestavení (GAC) můžete použít [nástroj globální sestavení mezipaměti (gacutil.exe) .NET](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="96bb6-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="96bb6-117">*Gacutil.exe* je pouze pro účely vývoje.</span><span class="sxs-lookup"><span data-stu-id="96bb6-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="96bb6-118">Nepoužívejte jej k instalaci produkčních sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="96bb6-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="96bb6-119">Syntaxe pro použití *gacutil.exe* k instalaci sestavení v globální mezipaměti sestavení (GAC) je následující:</span><span class="sxs-lookup"><span data-stu-id="96bb6-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="96bb6-120">V tomto příkazu *\<assembly name>* je název sestavení pro instalaci v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="96bb6-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="96bb6-121">Pokud *gacutil.exe* není v systémové cestě, použijte [příkazový řádek pro vývojáře pro vs *\<version>* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="96bb6-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="96bb6-122">Následující příklad nainstaluje sestavení s názvem souboru *hello.dll* do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="96bb6-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="96bb6-123">V dřívějších verzích .NET Framework rozhraní *Shfusion.dll* prostředí Windows umožňuje instalovat sestavení jejich přetažením do Průzkumníka souborů.</span><span class="sxs-lookup"><span data-stu-id="96bb6-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="96bb6-124">Počínaje .NET Framework 4 je *Shfusion.dll* zastaralé.</span><span class="sxs-lookup"><span data-stu-id="96bb6-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="96bb6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="96bb6-125">See also</span></span>

- [<span data-ttu-id="96bb6-126">Práce se sestaveními a globální mezipamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="96bb6-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="96bb6-127">Postupy: odebrání sestavení z globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="96bb6-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="96bb6-128">Gacutil.exe (nástroj globální mezipaměť sestavení)</span><span class="sxs-lookup"><span data-stu-id="96bb6-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="96bb6-129">Postupy: podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="96bb6-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
