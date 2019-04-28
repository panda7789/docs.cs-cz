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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705542"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="c4e07-102">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="c4e07-102">Programming with Assemblies</span></span>
<span data-ttu-id="c4e07-103">Sestavení jsou stavební kameny nástroje rozhraní .NET Framework. tvoří základní jednotku nasazení, správu verzí, opětovného použití, rozsahu platnosti při aktivaci a oprávnění zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="c4e07-104">Sestavení poskytuje modulu CLR (Common Language Runtime) informace, které požaduje pro zjištění typu implementace.</span><span class="sxs-lookup"><span data-stu-id="c4e07-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="c4e07-105">Jde o kolekci typů a prostředků, které jsou vytvořené pro spolupracovaly a tvořily logickou jednotku funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="c4e07-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="c4e07-106">V modulu runtime neexistuje typ mimo kontext sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="c4e07-107">Tato část popisuje, jak vytvářet moduly, vytvořit sestavení z modulů, vytvořte dvojici klíčů a podepsání sestavení silným názvem a instalace sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="c4e07-108">Kromě toho tato část popisuje způsob použití [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zobrazíte informace o manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4e07-109">Od verze rozhraní .NET Framework verze 2.0, nenačte modul runtime, který byl zkompilován s verzí rozhraní .NET Framework, která má vyšší číslo verze než aktuálně zavedený modul runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="c4e07-110">To platí pro kombinaci hlavní a vedlejší součásti číslo verze.</span><span class="sxs-lookup"><span data-stu-id="c4e07-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4e07-111">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c4e07-111">In This Section</span></span>  
 [<span data-ttu-id="c4e07-112">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="c4e07-113">Poskytuje přehled o jeden soubor a vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="c4e07-114">Názvy sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="c4e07-115">Poskytuje přehled o pojmenovávání sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="c4e07-116">Postupy: Určení plně kvalifikovaného názvu sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="c4e07-117">Popisuje, jak určit plně kvalifikovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="c4e07-118">Spouštění internetových aplikací v režimu plné důvěryhodnosti</span><span class="sxs-lookup"><span data-stu-id="c4e07-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="c4e07-119">Popisuje, jak určit starší verze zásad zabezpečení pro plně důvěryhodná sestavení ve sdílené složce intranetu.</span><span class="sxs-lookup"><span data-stu-id="c4e07-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="c4e07-120">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="c4e07-121">Poskytuje přehled o vyhledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="c4e07-122">Postupy: Sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="c4e07-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="c4e07-123">Popisuje postup vytvoření jednosouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="c4e07-124">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="c4e07-125">Popisuje důvody pro vytvoření vícesouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="c4e07-126">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="c4e07-127">Popisuje, jak vytvořit vícesouborové sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="c4e07-128">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="c4e07-129">Popisuje atributy sestavení a jejich nastavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="c4e07-130">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="c4e07-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="c4e07-131">Popisuje, jak a proč podepsání sestavení silným názvem a obsahuje témata s postupy.</span><span class="sxs-lookup"><span data-stu-id="c4e07-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="c4e07-132">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="c4e07-133">Popisuje, jak zpožděný podpis sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="c4e07-134">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="c4e07-135">Popisuje, jak a proč přidávání sestavení do globální mezipaměti sestavení a obsahuje témata s postupy.</span><span class="sxs-lookup"><span data-stu-id="c4e07-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="c4e07-136">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="c4e07-137">Popisuje způsob použití jazyka MSIL Disassembler (Ildasm.exe) k zobrazení obsahu sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="c4e07-138">Předávání typů v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="c4e07-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="c4e07-139">Popisuje, jak používat předávání typů pro přesunutí typu do jiného sestavení bez porušení existujících aplikací.</span><span class="sxs-lookup"><span data-stu-id="c4e07-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c4e07-140">Odkaz</span><span class="sxs-lookup"><span data-stu-id="c4e07-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="c4e07-141">Třída rozhraní .NET Framework, která představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c4e07-142">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c4e07-142">Related Sections</span></span>  
 [<span data-ttu-id="c4e07-143">Postupy: Získávání informací o člen typu a ze sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="c4e07-144">Popisuje, jak prostřednictvím kódu programu získání dalších informací o typu a ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="c4e07-145">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="c4e07-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="c4e07-146">Poskytuje koncepční přehled common language runtime sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="c4e07-147">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="c4e07-148">Obsahuje základní informace o prvku vazby sestavení a <xref:System.Reflection.AssemblyVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="c4e07-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="c4e07-149">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="c4e07-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="c4e07-150">Popisuje, jak modul runtime určuje sestavení, které použije ke splnění požadavků vazby.</span><span class="sxs-lookup"><span data-stu-id="c4e07-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="c4e07-151">Reflexe</span><span class="sxs-lookup"><span data-stu-id="c4e07-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="c4e07-152">Popisuje způsob použití **reflexe** třídy k získání informací o sestavení.</span><span class="sxs-lookup"><span data-stu-id="c4e07-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
