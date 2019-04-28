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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674984"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="87a5f-102">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="87a5f-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="87a5f-103">Globální mezipaměti sestavení (GAC) ukládá sestavení, které sdílí několik aplikací.</span><span class="sxs-lookup"><span data-stu-id="87a5f-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="87a5f-104">Instalace sestavení do [globální mezipaměti sestavení](gac.md) s jedním z následujících součástí:</span><span class="sxs-lookup"><span data-stu-id="87a5f-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 
- [<span data-ttu-id="87a5f-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="87a5f-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="87a5f-106">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="87a5f-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="87a5f-107">Nainstalujte pouze sestavení se silným názvem do mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="87a5f-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="87a5f-108">Informace o tom, jak vytvořit sestavení se silným názvem naleznete v tématu [jak: Podepsání sestavení silným názvem](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="87a5f-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="87a5f-109">Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="87a5f-109">Windows Installer</span></span>

<span data-ttu-id="87a5f-110">[Instalační program Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), instalace modulu Windows je doporučený způsob přidávání sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a5f-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="87a5f-111">Instalační služby systému Windows poskytuje možnost počítání odkazů sestavení v globální mezipaměti sestavení a další výhody.</span><span class="sxs-lookup"><span data-stu-id="87a5f-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="87a5f-112">Vytvoření instalačního balíčku pro Instalační služby systému Windows, použijte [WiX toolset rozšíření pro Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="87a5f-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="87a5f-113">Nástroj globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="87a5f-113">Global assembly cache tool</span></span>

<span data-ttu-id="87a5f-114">Můžete použít [nástroj globální mezipaměti sestavení (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidávání sestavení do globální mezipaměti sestavení a k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a5f-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="87a5f-115">*Gacutil.exe* je jenom pro účely vývoje.</span><span class="sxs-lookup"><span data-stu-id="87a5f-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="87a5f-116">Nepoužívejte ho k instalaci produkčních sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a5f-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="87a5f-117">Syntaxe pro používání *gacutil.exe* instalace sestavení do GAC vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="87a5f-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="87a5f-118">V tomto příkazu  *\<název sestavení >* je název sestavení, můžete nainstalovat v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a5f-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="87a5f-119">Pokud *gacutil.exe* není v systémové cestě, použijte [Developer Command Prompt for VS  *\<verze >*](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="87a5f-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="87a5f-120">Následující příklad nainstaluje sestavení s názvem souboru *hello.dll* do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="87a5f-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="87a5f-121">V dřívějších verzích rozhraní .NET Framework *Shfusion.dll* rozšíření prostředí Windows umožňují instalaci sestavení přetažením do Průzkumníka souborů.</span><span class="sxs-lookup"><span data-stu-id="87a5f-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="87a5f-122">Od verze rozhraní .NET Framework 4, *Shfusion.dll* je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="87a5f-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="87a5f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87a5f-123">See also</span></span>

- [<span data-ttu-id="87a5f-124">Práce se sestaveními a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="87a5f-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="87a5f-125">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="87a5f-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="87a5f-126">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="87a5f-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="87a5f-127">Postupy: Podepsání sestavení silným názvem</span><span class="sxs-lookup"><span data-stu-id="87a5f-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
