---
title: "Zprostředkovatel komunikace s objekty COM bez registrace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28ecb3419bddcc8e9a192b240a7bf90474314c1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="6310c-102">Zprostředkovatel komunikace s objekty COM bez registrace</span><span class="sxs-lookup"><span data-stu-id="6310c-102">Registration-Free COM Interop</span></span>
<span data-ttu-id="6310c-103">Spoluprací COM bez registrace se aktivuje komponentu bez uložení informací o sestavení pomocí registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6310c-103">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="6310c-104">Místo registrace komponenty v počítači během nasazení, vytvoření souborů manifestu Win32 stylu v době návrhu, které obsahují informace o aktivaci a vazeb.</span><span class="sxs-lookup"><span data-stu-id="6310c-104">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="6310c-105">Tyto soubory manifestu, nikoli klíče registru přímé aktivace objektu.</span><span class="sxs-lookup"><span data-stu-id="6310c-105">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="6310c-106">Použití bezregistrační aktivace pro vaše sestavení místo registrace je během nasazení nabízí dvě výhody:</span><span class="sxs-lookup"><span data-stu-id="6310c-106">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
-   <span data-ttu-id="6310c-107">Můžete řídit, které DLL verze knihovny se aktivuje, když více než jedna verze je nainstalovaná na počítači.</span><span class="sxs-lookup"><span data-stu-id="6310c-107">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
-   <span data-ttu-id="6310c-108">Koncoví uživatelé mohou používat XCOPY nebo FTP zkopírovat vaší aplikace do příslušného adresáře v počítači.</span><span class="sxs-lookup"><span data-stu-id="6310c-108">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="6310c-109">Aplikace pak spustíte z tohoto adresáře.</span><span class="sxs-lookup"><span data-stu-id="6310c-109">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="6310c-110">Tato část popisuje dva typy manifesty potřeba pro spolupráci s COM bez registrace: manifestů aplikace a součásti.</span><span class="sxs-lookup"><span data-stu-id="6310c-110">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="6310c-111">Tyto manifesty jsou soubory formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6310c-111">These manifests are XML files.</span></span> <span data-ttu-id="6310c-112">Manifest aplikace, který je vytvořen vývojář aplikací, obsahuje metadata, která popisuje sestavení a závislosti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6310c-112">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="6310c-113">Manifest součásti, vytvořené vývojář součást obsahuje informace, v opačném případě umístěny v registru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6310c-113">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="6310c-114">Požadavky pro spolupráci s COM bez registrace</span><span class="sxs-lookup"><span data-stu-id="6310c-114">Requirements for registration-free COM interop</span></span>  
  
1.  <span data-ttu-id="6310c-115">Podpora pro spoluprací COM bez registrace se mírně liší v závislosti na typu knihovny sestavení; Konkrétně, jestli je nespravované (COM-souběžného) nebo spravované sestavení (. NET-based).</span><span class="sxs-lookup"><span data-stu-id="6310c-115">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="6310c-116">V následující tabulce jsou uvedeny operačního systému a požadavky na verzi rozhraní .NET Framework pro každý typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="6310c-116">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="6310c-117">Typ sestavení</span><span class="sxs-lookup"><span data-stu-id="6310c-117">Assembly type</span></span>|<span data-ttu-id="6310c-118">Operační systém</span><span class="sxs-lookup"><span data-stu-id="6310c-118">Operating system</span></span>|<span data-ttu-id="6310c-119">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6310c-119">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="6310c-120">COM – souběžného</span><span class="sxs-lookup"><span data-stu-id="6310c-120">COM side-by-side</span></span>|<span data-ttu-id="6310c-121">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="6310c-121">Microsoft Windows XP</span></span>|<span data-ttu-id="6310c-122">Není požadováno.</span><span class="sxs-lookup"><span data-stu-id="6310c-122">Not required.</span></span>|  
    |<span data-ttu-id="6310c-123">. Na základě NET</span><span class="sxs-lookup"><span data-stu-id="6310c-123">.NET-based</span></span>|<span data-ttu-id="6310c-124">Windows XP s aktualizací SP2</span><span class="sxs-lookup"><span data-stu-id="6310c-124">Windows XP with SP2</span></span>|<span data-ttu-id="6310c-125">NET Framework verze 1.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="6310c-125">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="6310c-126">Řady Windows Server 2003 podporuje také spoluprací COM bez registrace pro. Na základě NET sestavení.</span><span class="sxs-lookup"><span data-stu-id="6310c-126">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="6310c-127">Pro. Na základě NET třída být kompatibilní s registru bez aktivace z modelu COM, třídu musí mít výchozí konstruktor a musí být veřejné.</span><span class="sxs-lookup"><span data-stu-id="6310c-127">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a default constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="6310c-128">Konfigurace komponenty modelu COM bez registrace aktivace</span><span class="sxs-lookup"><span data-stu-id="6310c-128">Configuring COM components for registration-free activation</span></span>  
  
1.  <span data-ttu-id="6310c-129">Pro komponenty modelu COM se účastnit bezregistrační aktivace musí být nasazený jako souběžně sdílená sestavení.</span><span class="sxs-lookup"><span data-stu-id="6310c-129">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="6310c-130">Souběžně sdílená sestavení jsou nespravované sestavení.</span><span class="sxs-lookup"><span data-stu-id="6310c-130">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="6310c-131">Další informace najdete v tématu [pomocí souběžně sdílená sestavení](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="6310c-131">For more information, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
     <span data-ttu-id="6310c-132">Chcete-li používat souběžně sdílená sestavení COM,. Aplikace založené na NET vývojář musí poskytnout manifest aplikace, který obsahuje informace o aktivaci a vazeb.</span><span class="sxs-lookup"><span data-stu-id="6310c-132">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="6310c-133">Podpora pro nespravovaná souběžně sdílená sestavení je integrovaná do operačního systému Windows XP.</span><span class="sxs-lookup"><span data-stu-id="6310c-133">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="6310c-134">Modul runtime COM, nepodporuje operační systém, prohledává manifest aplikace pro informace o aktivaci k aktivované součást není v registru.</span><span class="sxs-lookup"><span data-stu-id="6310c-134">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="6310c-135">Bezregistrační aktivace je volitelný pro komponenty modelu COM, které jsou nainstalované v systému Windows XP.</span><span class="sxs-lookup"><span data-stu-id="6310c-135">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="6310c-136">Podrobné pokyny k přidání souběžně sdílená sestavení do aplikace, najdete v části [pomocí souběžně sdílená sestavení](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="6310c-136">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6310c-137">Souběžného zpracování se funkce rozhraní .NET Framework, která umožňuje více verzí modulu runtime a více verzí aplikací a součástí, které používají verzi modulu runtime ve stejnou dobu běžela na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="6310c-137">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="6310c-138">Spuštění vedle sebe a souběžně sdílená sestavení jsou různé mechanismy pro zajištění funkcí vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="6310c-138">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6310c-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="6310c-139">See Also</span></span>  
 [<span data-ttu-id="6310c-140">Postupy: Konfigurace Bezregistrační aktivace rozhraní .NET Framework na základě COM – součásti</span><span class="sxs-lookup"><span data-stu-id="6310c-140">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
