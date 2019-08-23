---
title: Programování se sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921423"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="7aa0b-102">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="7aa0b-102">Programming with Assemblies</span></span>
<span data-ttu-id="7aa0b-103">Sestavení jsou stavebními bloky .NET Framework; tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="7aa0b-104">Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="7aa0b-105">Jedná se o kolekci typů a prostředků, které jsou sestaveny tak, aby spolupracovaly a tvořily logickou jednotku funkcí.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="7aa0b-106">V modulu runtime neexistuje typ mimo kontext sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="7aa0b-107">Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořit pár klíčů a podepsat sestavení se silným názvem a nainstalovat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="7aa0b-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="7aa0b-108">Kromě toho tato část popisuje, jak použít [jazyk MSIL Disassembler (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7aa0b-109">Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="7aa0b-110">To platí pro kombinaci hlavních a vedlejších součástí čísla verze.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7aa0b-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="7aa0b-111">In This Section</span></span>  
 [<span data-ttu-id="7aa0b-112">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="7aa0b-113">Poskytuje přehled o jednom souboru a vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="7aa0b-114">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="7aa0b-115">Poskytuje přehled o pojmenovávání sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="7aa0b-116">Postupy: Určení plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="7aa0b-117">Popisuje, jak určit plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="7aa0b-118">Spouštění internetových aplikací v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="7aa0b-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="7aa0b-119">Popisuje, jak zadat starší zásady zabezpečení pro sestavení s úplným vztahem důvěryhodnosti pro sdílenou složku v intranetu.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="7aa0b-120">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="7aa0b-121">Poskytuje přehled o tom, kde najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="7aa0b-122">Postupy: Sestavení jednoho souboru sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="7aa0b-123">Popisuje, jak vytvořit sestavení s jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="7aa0b-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="7aa0b-125">Popisuje důvody pro vytváření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="7aa0b-126">Postupy: Sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="7aa0b-127">Popisuje, jak vytvořit vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="7aa0b-128">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="7aa0b-129">Popisuje atributy sestavení a jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="7aa0b-130">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="7aa0b-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="7aa0b-131">Popisuje, jak a proč podepsat sestavení silným názvem a obsahuje postupy pro témata.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="7aa0b-132">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="7aa0b-133">Popisuje, jak zpozdit podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="7aa0b-134">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="7aa0b-135">Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení (GAC) a obsahuje postupy pro témata.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="7aa0b-136">Postupy: Zobrazit obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="7aa0b-137">Popisuje, jak použít jazyk MSIL Disassembler (Ildasm. exe) k zobrazení obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="7aa0b-138">Předávání typů v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="7aa0b-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="7aa0b-139">Popisuje, jak použít přesměrování typu k přesunutí typu do jiného sestavení bez přerušení stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7aa0b-140">Reference</span><span class="sxs-lookup"><span data-stu-id="7aa0b-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="7aa0b-141">Třída .NET Framework, která představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7aa0b-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="7aa0b-142">Related Sections</span></span>  
 [<span data-ttu-id="7aa0b-143">Postupy: Získání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="7aa0b-144">Popisuje, jak programově získat typ a další informace ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="7aa0b-145">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="7aa0b-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="7aa0b-146">Poskytuje koncepční přehled sestavení společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="7aa0b-147">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="7aa0b-148">Poskytuje přehled vazby sestavení a <xref:System.Reflection.AssemblyVersionAttribute> atributů a. <xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="7aa0b-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="7aa0b-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7aa0b-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="7aa0b-150">Popisuje způsob, jakým modul runtime určuje, které sestavení se má použít ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="7aa0b-151">Reflexe</span><span class="sxs-lookup"><span data-stu-id="7aa0b-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="7aa0b-152">Popisuje způsob použití třídy reflexe k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="7aa0b-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
