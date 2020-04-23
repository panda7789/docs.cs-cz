---
title: 'Postupy: Odebrání sestavení z globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
ms.openlocfilehash: c7d85222f35a61154e3eec70d8c9dad2ca6a32f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119856"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="9e7b8-102">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9e7b8-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="9e7b8-103">Existují dva způsoby, jak odebrat sestavení z globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="9e7b8-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="9e7b8-104">Pomocí [nástroje Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9e7b8-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="9e7b8-105">Tuto možnost můžete použít k odinstalování sestavení, která jste umístili do GAC během vývoje a testování.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="9e7b8-106">Pomocí [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="9e7b8-106">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="9e7b8-107">Tuto možnost byste měli použít k odinstalování sestavení při testování instalačních balíčků a pro produkční systémy.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="9e7b8-108">Odebrání sestavení pomocí Gacutil. exe</span><span class="sxs-lookup"><span data-stu-id="9e7b8-108">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="9e7b8-109">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9e7b8-109">At the command prompt, type the following command:</span></span>

<span data-ttu-id="9e7b8-110">*název sestavení* pro **Gacutil – u** \<></span><span class="sxs-lookup"><span data-stu-id="9e7b8-110">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="9e7b8-111">V tomto příkazu je *název sestavení* název sestavení, které chcete odebrat z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9e7b8-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="9e7b8-112">Nástroj Gacutil. exe by neměl být použit k odebrání sestavení v produkčních systémech z důvodu možnosti, že sestavení může být stále vyžadováno určitou aplikací.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="9e7b8-113">Místo toho byste měli použít Instalační služba systému Windows, které udržují počet odkazů pro každé sestavení, které je nainstalováno v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9e7b8-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="9e7b8-114">Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="9e7b8-114">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="9e7b8-115">Odebrání sestavení pomocí Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="9e7b8-115">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="9e7b8-116">V aplikaci **a funkce** v **Ovládacích panelech**vyberte aplikaci, kterou chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="9e7b8-117">Pokud instalační balíček umístil sestavení do globální mezipaměti sestavení (GAC), Instalační služba systému Windows je odebere, pokud nejsou používány jinou aplikací.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="9e7b8-118">Instalační služba systému Windows udržuje počet odkazů pro sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9e7b8-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="9e7b8-119">Sestavení je odebráno z GAC pouze v případě, že počet odkazů dosáhne nuly, což znamená, že není používáno žádnou aplikací nainstalovanou Instalační služba systému Windows balíčkem.</span><span class="sxs-lookup"><span data-stu-id="9e7b8-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e7b8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e7b8-120">See also</span></span>

- [<span data-ttu-id="9e7b8-121">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="9e7b8-121">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="9e7b8-122">Postupy: Instalace sestavení do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="9e7b8-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="9e7b8-123">Gacutil. exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="9e7b8-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
