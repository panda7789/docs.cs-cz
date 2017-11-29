---
title: "Pokyny pro vytváření komponent pro souběžné spouštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 054744612ec54861f675005a27a309e00024b242
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a><span data-ttu-id="50f82-102">Pokyny pro vytváření komponent pro souběžné spouštění</span><span class="sxs-lookup"><span data-stu-id="50f82-102">Guidelines for Creating Components for Side-by-Side Execution</span></span>
<span data-ttu-id="50f82-103">Dodržujte následující obecné pokyny k vytvoření spravované aplikace nebo součásti určené pro spuštění vedle sebe:</span><span class="sxs-lookup"><span data-stu-id="50f82-103">Follow these general guidelines to create managed applications or components designed for side-by-side execution:</span></span>  
  
-   <span data-ttu-id="50f82-104">Typ identity vazbu na konkrétní verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="50f82-104">Bind type identity to a particular version of a file.</span></span>  
  
     <span data-ttu-id="50f82-105">Modul common language runtime sváže identitu typu určitého souboru verze pomocí sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="50f82-105">The common language runtime binds type identity to a particular file version by using strong-named assemblies.</span></span> <span data-ttu-id="50f82-106">Pokud chcete vytvořit aplikace nebo součásti pro spuštění vedle sebe, musí dát všechna sestavení silným názvem.</span><span class="sxs-lookup"><span data-stu-id="50f82-106">To create an application or component for side-by-side execution, you must give all assemblies a strong name.</span></span> <span data-ttu-id="50f82-107">Tím se vytvoří přesné typ identity a zajistí, že všechny typu řešení směřuje na správný soubor.</span><span class="sxs-lookup"><span data-stu-id="50f82-107">This creates precise type identity and ensures that any type resolution is directed to the correct file.</span></span> <span data-ttu-id="50f82-108">Sestavení se silným názvem obsahuje verze, jazykové verze a vydavatele informace, které používá modul runtime najít správný soubor ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="50f82-108">A strong-named assembly contains version, culture, and publisher information that the runtime uses to locate the correct file to fulfill a binding request.</span></span>  
  
-   <span data-ttu-id="50f82-109">Použijte používající verzi úložiště.</span><span class="sxs-lookup"><span data-stu-id="50f82-109">Use version-aware storage.</span></span>  
  
     <span data-ttu-id="50f82-110">K poskytování úložiště používající verzi modulu runtime používá globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="50f82-110">The runtime uses the global assembly cache to provide version-aware storage.</span></span> <span data-ttu-id="50f82-111">Globální mezipaměť sestavení je používající verzi adresářová struktura nainstalována v každém počítači, který používá rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50f82-111">The global assembly cache is a version-aware directory structure installed on every computer that uses the .NET Framework.</span></span> <span data-ttu-id="50f82-112">Sestavení, které jsou nainstalované v globální mezipaměti sestavení se nepřepíšou při instalaci nové verze této položky assembly.</span><span class="sxs-lookup"><span data-stu-id="50f82-112">Assemblies installed in the global assembly cache are not overwritten when a new version of that assembly is installed.</span></span>  
  
-   <span data-ttu-id="50f82-113">Vytvoření aplikace nebo součásti, které běží izolovaně.</span><span class="sxs-lookup"><span data-stu-id="50f82-113">Create an application or component that runs in isolation.</span></span>  
  
     <span data-ttu-id="50f82-114">Aplikace nebo součásti, který spouští v izolaci musí spravovat prostředky, aby nedocházelo ke konfliktům, když dvě instance aplikací nebo součástí běží současně.</span><span class="sxs-lookup"><span data-stu-id="50f82-114">An application or component that runs in isolation must manage resources to avoid conflicts when two instances of the application or component are running simultaneously.</span></span> <span data-ttu-id="50f82-115">Aplikace nebo součásti, musíte taky použít struktury specifické pro verzi souborů.</span><span class="sxs-lookup"><span data-stu-id="50f82-115">The application or component must also use a version-specific file structure.</span></span>  
  
## <a name="application-and-component-isolation"></a><span data-ttu-id="50f82-116">Aplikace a součásti izolace</span><span class="sxs-lookup"><span data-stu-id="50f82-116">Application and Component Isolation</span></span>  
 <span data-ttu-id="50f82-117">Jednoho klíče na úspěšně návrhu aplikace nebo součásti pro spuštění vedle sebe je izolace.</span><span class="sxs-lookup"><span data-stu-id="50f82-117">One key to successfully designing an application or component for side-by-side execution is isolation.</span></span> <span data-ttu-id="50f82-118">Aplikace nebo součásti musí spravovat všechny prostředky, zejména souboru vstupně-výstupních operací, izolovaně.</span><span class="sxs-lookup"><span data-stu-id="50f82-118">The application or component must manage all resources, particularly file I/O, in an isolated manner.</span></span> <span data-ttu-id="50f82-119">Postupujte podle těchto pokynů, abyste měli jistotu, že vaše aplikace nebo součásti spouští v izolaci:</span><span class="sxs-lookup"><span data-stu-id="50f82-119">Follow these guidelines to make sure your application or component runs in isolation:</span></span>  
  
-   <span data-ttu-id="50f82-120">Zápis do registru způsobem specifické pro verzi.</span><span class="sxs-lookup"><span data-stu-id="50f82-120">Write to the registry in a version-specific way.</span></span> <span data-ttu-id="50f82-121">Ukládání hodnot podregistrů nebo klíče, které určují verze a mezi verzemi součásti nesdílí informace o stavu nebo stavu.</span><span class="sxs-lookup"><span data-stu-id="50f82-121">Store values in hives or keys that indicate the version, and do not share information or state across versions of a component.</span></span> <span data-ttu-id="50f82-122">Tím se zabrání dvě aplikace nebo součásti, které jsou spuštěné ve stejnou dobu ze přepsal informace.</span><span class="sxs-lookup"><span data-stu-id="50f82-122">This prevents two applications or components running at the same time from overwriting information.</span></span>  
  
-   <span data-ttu-id="50f82-123">Zajistěte objektů s názvem jádra specifické pro verzi, takže časování nedojde.</span><span class="sxs-lookup"><span data-stu-id="50f82-123">Make named kernel objects version-specific so that a race condition does not occur.</span></span> <span data-ttu-id="50f82-124">Například časování nastane, když dvě semaforů z dvě verze stejné aplikace čekat na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="50f82-124">For example, a race condition occurs when two semaphores from two versions of the same application wait on each other.</span></span>  
  
-   <span data-ttu-id="50f82-125">Zkontrolujte názvy souborů a adresářů využívající technologii verze.</span><span class="sxs-lookup"><span data-stu-id="50f82-125">Make file and directory names version-aware.</span></span> <span data-ttu-id="50f82-126">To znamená, že se soubor struktury spoléhají na informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="50f82-126">This means that file structures should rely on version information.</span></span>  
  
-   <span data-ttu-id="50f82-127">Vytvořte uživatelské účty a skupiny způsobem specifické pro verzi.</span><span class="sxs-lookup"><span data-stu-id="50f82-127">Create user accounts and groups in a version-specific manner.</span></span> <span data-ttu-id="50f82-128">Uživatelské účty a skupiny vytvořené aplikace, mělo by být určené verzí.</span><span class="sxs-lookup"><span data-stu-id="50f82-128">User accounts and groups created by an application should be identified by version.</span></span> <span data-ttu-id="50f82-129">Nesdílí uživatelské účty a skupiny mezi verzemi aplikace.</span><span class="sxs-lookup"><span data-stu-id="50f82-129">Do not share user accounts and groups between versions of an application.</span></span>  
  
## <a name="installing-and-uninstalling-versions"></a><span data-ttu-id="50f82-130">Instalace a odinstalace verze</span><span class="sxs-lookup"><span data-stu-id="50f82-130">Installing and Uninstalling Versions</span></span>  
 <span data-ttu-id="50f82-131">Při navrhování aplikace pro spuštění vedle sebe, dodržujte následující pokyny týkající se instalace a odinstalace verze:</span><span class="sxs-lookup"><span data-stu-id="50f82-131">When designing an application for side-by-side execution, follow these guidelines concerning installing and uninstalling versions:</span></span>  
  
-   <span data-ttu-id="50f82-132">Neodstraňujte informace z registru, který může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50f82-132">Do not delete information from the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="50f82-133">Nepřepisovat existující informace v registru, který může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50f82-133">Do not replace information in the registry that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="50f82-134">Nelze zrušit registraci komponenty modelu COM, které může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50f82-134">Do not unregister COM components that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="50f82-135">Neměňte **InprocServer32** nebo jiné položky registru pro server COM, která již byla zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="50f82-135">Do not change **InprocServer32** or other registry entries for a COM server that was already registered.</span></span>  
  
-   <span data-ttu-id="50f82-136">Neodstraňujte uživatelské účty nebo skupiny, které může být potřeba pomocí dalších aplikací běžících v rámci jinou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50f82-136">Do not delete user accounts or groups that may be needed by other applications running under a different version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="50f82-137">Nepřidávejte nic do registru, který obsahuje cestu bez uvedené verze.</span><span class="sxs-lookup"><span data-stu-id="50f82-137">Do not add anything to the registry that contains an unversioned path.</span></span>  
  
## <a name="file-version-number-and-assembly-version-number"></a><span data-ttu-id="50f82-138">Číslo verze souboru a číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="50f82-138">File Version Number and Assembly Version Number</span></span>  
 <span data-ttu-id="50f82-139">Verze souboru je prostředek verze Win32, který se nepoužívá modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="50f82-139">File version is a Win32 version resource that is not used by the runtime.</span></span> <span data-ttu-id="50f82-140">Obecně platí aktualizujte verzi souboru i pro aktualizaci na místě.</span><span class="sxs-lookup"><span data-stu-id="50f82-140">In general, you update the file version even for an in-place update.</span></span> <span data-ttu-id="50f82-141">Dva identické soubory může obsahovat informace o verzi jiný soubor, a dva různé soubory mohou mít stejné informace o verzi souboru.</span><span class="sxs-lookup"><span data-stu-id="50f82-141">Two identical files can have different file version information, and two different files can have the same file version information.</span></span>  
  
 <span data-ttu-id="50f82-142">Verze sestavení se používá modulem runtime pro sestavení – vazby.</span><span class="sxs-lookup"><span data-stu-id="50f82-142">The assembly version is used by the runtime for assembly binding.</span></span> <span data-ttu-id="50f82-143">Dva identické sestavení pomocí různých čísel verzí jsou považovány za dvě různé sestavení modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="50f82-143">Two identical assemblies with different version numbers are treated as two different assemblies by the runtime.</span></span>  
  
 <span data-ttu-id="50f82-144">[Nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) můžete nahradit sestavení při pouze čísla verze souboru je novější.</span><span class="sxs-lookup"><span data-stu-id="50f82-144">The [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) allows you to replace an assembly when only the file version number is newer.</span></span> <span data-ttu-id="50f82-145">Instalační program obecně instalací sestavení Pokud číslo verze sestavení je větší.</span><span class="sxs-lookup"><span data-stu-id="50f82-145">The installer generally does not install over an assembly unless the assembly version number is greater.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f82-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f82-146">See Also</span></span>  
 [<span data-ttu-id="50f82-147">Spuštění vedle sebe</span><span class="sxs-lookup"><span data-stu-id="50f82-147">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)  
 [<span data-ttu-id="50f82-148">Postupy: povolení a zákaz automatického přesměrování vazby</span><span class="sxs-lookup"><span data-stu-id="50f82-148">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
