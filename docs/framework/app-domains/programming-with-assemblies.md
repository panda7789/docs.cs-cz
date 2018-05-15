---
title: Programování se sestaveními
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="1fd30-102">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="1fd30-102">Programming with Assemblies</span></span>
<span data-ttu-id="1fd30-103">Sestavení jsou stavebními bloky rozhraní .NET Framework; tvoří základní jednotku nasazení, Správa verzí, opakované použití, aktivaci oborů a oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="1fd30-104">Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace.</span><span class="sxs-lookup"><span data-stu-id="1fd30-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="1fd30-105">Jedná se o kolekci typů a prostředků, které jsou vytvořeny a společně tvoří logickou jednotku funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="1fd30-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="1fd30-106">V modulu runtime neexistuje typ mimo kontext sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="1fd30-107">Tato část popisuje, jak vytvořit moduly, vytvořit sestavení z modulů, vytvořte dvojici klíčů a podepsání sestavení se silným názvem a instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="1fd30-108">Kromě toho tato část popisuje postup použití [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací o manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fd30-109">Od verze rozhraní .NET Framework verze 2.0, modul runtime nenačte sestavení, které bylo kompilováno s verzi rozhraní .NET Framework, který má vyšší číslo verze než aktuálně načtených modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="1fd30-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="1fd30-110">To platí pro soubor součástí hlavní a vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="1fd30-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fd30-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1fd30-111">In This Section</span></span>  
 [<span data-ttu-id="1fd30-112">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="1fd30-113">Poskytuje přehled o jeden soubor a vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="1fd30-114">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="1fd30-115">Poskytuje přehled o pojmenování sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="1fd30-116">Postupy: Určení plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="1fd30-117">Popisuje, jak určit plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="1fd30-118">Spouštění internetových aplikací v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="1fd30-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="1fd30-119">Popisuje, jak zadat starší verze zásad zabezpečení pro sestavení plné důvěryhodnosti ve sdílené složce intranetu.</span><span class="sxs-lookup"><span data-stu-id="1fd30-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="1fd30-120">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="1fd30-121">Poskytuje přehled o umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="1fd30-122">Postupy: Vytváření sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="1fd30-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="1fd30-123">Popisuje, jak vytvořit jeden soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="1fd30-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="1fd30-125">Popisuje důvody pro vytváření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="1fd30-126">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="1fd30-127">Popisuje postup vytvoření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="1fd30-128">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="1fd30-129">Popisuje atributů sestavení a jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="1fd30-130">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="1fd30-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="1fd30-131">Popisuje, jak a proč podepsání sestavení se silným názvem a obsahuje témata s postupy.</span><span class="sxs-lookup"><span data-stu-id="1fd30-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="1fd30-132">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="1fd30-133">Popisuje postup zpoždění podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="1fd30-134">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="1fd30-135">Popisuje, jak a proč přidat sestavení do globální mezipaměti sestavení a obsahuje témata s postupy.</span><span class="sxs-lookup"><span data-stu-id="1fd30-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="1fd30-136">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="1fd30-137">Popisuje, jak používat MSIL Disassembler (Ildasm.exe) k zobrazení obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="1fd30-138">Předávání typů v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="1fd30-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="1fd30-139">Popisuje, jak používat předávání typů typu přesunout do jiného sestavení bez porušení existujících aplikací.</span><span class="sxs-lookup"><span data-stu-id="1fd30-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1fd30-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1fd30-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="1fd30-141">Třída rozhraní .NET Framework, která představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1fd30-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1fd30-142">Related Sections</span></span>  
 [<span data-ttu-id="1fd30-143">Postupy: Získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="1fd30-144">Popisuje, jak programově získat typ a další informace z sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="1fd30-145">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="1fd30-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="1fd30-146">Poskytuje koncepční přehled common language runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="1fd30-147">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="1fd30-148">Poskytuje přehled vlastností sestavení – vazby a <xref:System.Reflection.AssemblyVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="1fd30-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="1fd30-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="1fd30-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="1fd30-150">Popisuje, jak modul runtime určuje sestavení, které použije ke splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="1fd30-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="1fd30-151">Reflexe</span><span class="sxs-lookup"><span data-stu-id="1fd30-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="1fd30-152">Popisuje postup použití **reflexe** třída získat informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="1fd30-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
