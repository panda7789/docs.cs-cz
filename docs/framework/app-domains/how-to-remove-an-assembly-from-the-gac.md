---
title: 'Postupy: Odebrání sestavení z globální mezipaměti sestavení'
description: Naučte se, jak odebrat sestavení z globální mezipaměti sestavení (GAC) v rozhraní .NET pomocí nástroje Global Assembly Cache (Gacutil.exe) nebo Instalační služba systému Windows.
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
ms.openlocfilehash: e3a596ea6029ded190c33032e96b601de9d4012d
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104771"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="85a8c-103">Postupy: Odebrání sestavení z globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="85a8c-103">How to: Remove an Assembly from the Global Assembly Cache</span></span>

<span data-ttu-id="85a8c-104">Existují dva způsoby, jak odebrat sestavení z globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="85a8c-104">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>

- <span data-ttu-id="85a8c-105">Pomocí [nástroje globální mezipaměť sestavení (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="85a8c-105">By using the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="85a8c-106">Tuto možnost můžete použít k odinstalování sestavení, která jste umístili do GAC během vývoje a testování.</span><span class="sxs-lookup"><span data-stu-id="85a8c-106">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>

- <span data-ttu-id="85a8c-107">Pomocí [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal).</span><span class="sxs-lookup"><span data-stu-id="85a8c-107">By using [Windows Installer](/windows/desktop/Msi/windows-installer-portal).</span></span> <span data-ttu-id="85a8c-108">Tuto možnost byste měli použít k odinstalování sestavení při testování instalačních balíčků a pro produkční systémy.</span><span class="sxs-lookup"><span data-stu-id="85a8c-108">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>

## <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="85a8c-109">Odebrání sestavení pomocí Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="85a8c-109">Removing an assembly with Gacutil.exe</span></span>

<span data-ttu-id="85a8c-110">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="85a8c-110">At the command prompt, type the following command:</span></span>

<span data-ttu-id="85a8c-111">**Gacutil – u**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="85a8c-111">**gacutil –u** \<*assembly name*></span></span>

<span data-ttu-id="85a8c-112">V tomto příkazu je *název sestavení* název sestavení, které chcete odebrat z globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="85a8c-112">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>

> [!WARNING]
> <span data-ttu-id="85a8c-113">Nepoužívejte Gacutil.exe k odebrání sestavení v produkčních systémech z důvodu možnosti, že sestavení může být stále vyžadováno v některé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85a8c-113">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="85a8c-114">Místo toho byste měli použít Instalační služba systému Windows, které udržují počet odkazů pro každé sestavení, které je nainstalováno v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="85a8c-114">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>

<span data-ttu-id="85a8c-115">Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="85a8c-115">The following example removes an assembly named `hello.dll` from the global assembly cache:</span></span>

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="85a8c-116">Odebrání sestavení pomocí Instalační služba systému Windows</span><span class="sxs-lookup"><span data-stu-id="85a8c-116">Removing an assembly with Windows Installer</span></span>

<span data-ttu-id="85a8c-117">V aplikaci **a funkce** v **Ovládacích panelech**vyberte aplikaci, kterou chcete odinstalovat.</span><span class="sxs-lookup"><span data-stu-id="85a8c-117">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="85a8c-118">Pokud instalační balíček umístil sestavení do globální mezipaměti sestavení (GAC), Instalační služba systému Windows je odebere, pokud nejsou používány jinou aplikací.</span><span class="sxs-lookup"><span data-stu-id="85a8c-118">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>

> [!NOTE]
> <span data-ttu-id="85a8c-119">Instalační služba systému Windows udržuje počet odkazů pro sestavení nainstalovaná v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="85a8c-119">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="85a8c-120">Sestavení je odebráno z GAC pouze v případě, že počet odkazů dosáhne nuly, což znamená, že není používáno žádnou aplikací nainstalovanou Instalační služba systému Windows balíčkem.</span><span class="sxs-lookup"><span data-stu-id="85a8c-120">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>

## <a name="see-also"></a><span data-ttu-id="85a8c-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="85a8c-121">See also</span></span>

- [<span data-ttu-id="85a8c-122">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="85a8c-122">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="85a8c-123">Postupy: Instalace sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="85a8c-123">How to: Install an Assembly into the Global Assembly Cache</span></span>](install-assembly-into-gac.md)
- [<span data-ttu-id="85a8c-124">Gacutil.exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="85a8c-124">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
