---
title: Programování se sestaveními
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
ms.openlocfilehash: 9f07d36d9e47189d53e367fd1406e5684c024aa3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107059"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="16f27-102">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="16f27-102">Program with assemblies</span></span>
<span data-ttu-id="16f27-103">Sestavení jsou stavebními bloky .NET Framework; tvoří základní jednotku nasazení, řízení verze, opětovné použití, rozsah aktivace a oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="16f27-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="16f27-104">Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace.</span><span class="sxs-lookup"><span data-stu-id="16f27-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="16f27-105">Jedná se o kolekci typů a prostředků, které jsou sestaveny tak, aby spolupracovaly a tvořily logickou jednotku funkcí.</span><span class="sxs-lookup"><span data-stu-id="16f27-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="16f27-106">V modulu runtime neexistuje typ mimo kontext sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="16f27-107">Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořit pár klíčů a podepsat sestavení se silným názvem a nainstalovat sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="16f27-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="16f27-108">Kromě toho tato část popisuje, jak použít [jazyk MSIL Disassembler (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16f27-109">Počínaje verzí 2,0 .NET Framework modul runtime nenačte sestavení, které bylo zkompilováno s verzí .NET Framework, která má vyšší číslo verze než aktuálně načtený modul runtime.</span><span class="sxs-lookup"><span data-stu-id="16f27-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="16f27-110">To platí pro kombinaci hlavních a vedlejších součástí čísla verze.</span><span class="sxs-lookup"><span data-stu-id="16f27-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="16f27-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="16f27-111">In this section</span></span>  
 [<span data-ttu-id="16f27-112">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="16f27-113">Poskytuje přehled o jednom souboru a vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="16f27-114">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="16f27-115">Poskytuje přehled o pojmenovávání sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="16f27-116">Postupy: určení plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="16f27-117">Popisuje, jak určit plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="16f27-118">Spouštění intranetových aplikací v úplném vztahu důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="16f27-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="16f27-119">Popisuje, jak zadat starší zásady zabezpečení pro sestavení s úplným vztahem důvěryhodnosti pro sdílenou složku v intranetu.</span><span class="sxs-lookup"><span data-stu-id="16f27-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="16f27-120">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="16f27-121">Poskytuje přehled o tom, kde najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="16f27-122">Postupy: sestavení sestavení s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="16f27-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="16f27-123">Popisuje, jak vytvořit sestavení s jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="16f27-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="16f27-124">Vícesouborové sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="16f27-125">Popisuje důvody pro vytváření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="16f27-126">Postupy: sestavení vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="16f27-127">Popisuje, jak vytvořit vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="16f27-128">Nastavit atributy sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="16f27-129">Popisuje atributy sestavení a jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="16f27-130">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="16f27-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="16f27-131">Popisuje, jak a proč podepsat sestavení silným názvem a obsahuje postupy pro témata.</span><span class="sxs-lookup"><span data-stu-id="16f27-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="16f27-132">Zpožděný podpis sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="16f27-133">Popisuje, jak zpozdit podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="16f27-134">Práce se sestaveními a globální mezipamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="16f27-135">Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení (GAC) a obsahuje postupy pro témata.</span><span class="sxs-lookup"><span data-stu-id="16f27-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="16f27-136">Postupy: zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="16f27-137">Popisuje, jak použít jazyk MSIL Disassembler (Ildasm. exe) k zobrazení obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="16f27-138">Předávání typů v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="16f27-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="16f27-139">Popisuje, jak použít přesměrování typu k přesunutí typu do jiného sestavení bez přerušení stávajících aplikací.</span><span class="sxs-lookup"><span data-stu-id="16f27-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="16f27-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="16f27-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="16f27-141">Třída .NET Framework, která představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="16f27-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="16f27-142">Related sections</span></span>  
 [<span data-ttu-id="16f27-143">Postupy: získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="16f27-144">Popisuje, jak programově získat typ a další informace ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="16f27-145">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="16f27-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="16f27-146">Poskytuje koncepční přehled sestavení společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="16f27-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="16f27-147">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="16f27-148">Poskytuje přehled vazby sestavení a atributů <xref:System.Reflection.AssemblyVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="16f27-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="16f27-149">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="16f27-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="16f27-150">Popisuje způsob, jakým modul runtime určuje, které sestavení se má použít ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="16f27-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="16f27-151">  [reflexe](../../framework/reflection-and-codedom/reflection.md)</span><span class="sxs-lookup"><span data-stu-id="16f27-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="16f27-152">Popisuje způsob použití třídy **reflexe** k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="16f27-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
