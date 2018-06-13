---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758123"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="48207-102">Postupy: Vytváření zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="48207-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="48207-103">Dodavatelé sestavení může stavu, že aplikace by měly používat na novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradovaná sestavením.</span><span class="sxs-lookup"><span data-stu-id="48207-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="48207-104">Soubor zásad vydavatele určuje sestavení – přesměrování a základní nastavení kódu a používá stejný formát jako konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="48207-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="48207-105">Soubor zásad vydavatele je zkompilován do sestavení a umístit do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="48207-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="48207-106">Součástí procesu vytváření zásad vydavatele existují tři kroky:</span><span class="sxs-lookup"><span data-stu-id="48207-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="48207-107">Vytvořte soubor zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="48207-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="48207-108">Vytvořte sestavení zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="48207-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="48207-109">Sestavení zásady vydavatele přidáte do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="48207-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="48207-110">Schéma pro vydavatele zásady je popsáno v [přesměrování verzí sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="48207-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="48207-111">Následující příklad ukazuje vydavatel soubor zásad, který přesměruje jednu verzi `myAssembly` do jiného.</span><span class="sxs-lookup"><span data-stu-id="48207-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="48207-112">Další informace o zadání základu kódu najdete v tématu [určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="48207-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="48207-113">Vytváření sestavení zásady vydavatele</span><span class="sxs-lookup"><span data-stu-id="48207-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="48207-114">Použití [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) vytvořit sestavení zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="48207-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="48207-115">Chcete-li vytvořit sestavení zásady vydavatele</span><span class="sxs-lookup"><span data-stu-id="48207-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="48207-116">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="48207-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="48207-117">**Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="48207-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="48207-118">V tomto příkazu:</span><span class="sxs-lookup"><span data-stu-id="48207-118">In this command:</span></span>  
  
    -   <span data-ttu-id="48207-119">*PublisherPolicyFile* argument je název souboru zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="48207-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="48207-120">*PublisherPolicyAssemblyFile* argument je název sestavení zásady vydavatele, který je výsledkem tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="48207-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="48207-121">Název souboru sestavení musí mít formát:</span><span class="sxs-lookup"><span data-stu-id="48207-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="48207-122">**zásady.**</span><span class="sxs-lookup"><span data-stu-id="48207-122">**policy.**</span></span> <span data-ttu-id="48207-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="48207-123">*majorNumber* **.**</span></span> <span data-ttu-id="48207-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="48207-124">*minorNumber* **.**</span></span> <span data-ttu-id="48207-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="48207-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="48207-126">*KeyPairFile* argument je název souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="48207-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="48207-127">Musíte se odhlásit sestavení a sestavení zásady vydavatele pomocí stejného páru klíčů.</span><span class="sxs-lookup"><span data-stu-id="48207-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="48207-128">*ProcessorArchitecture* argument identifikuje platformou cílem sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="48207-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="48207-129">Možnost cíle architekturu konkrétní procesoru je v rozhraní .NET Framework verze 2.0 nová.</span><span class="sxs-lookup"><span data-stu-id="48207-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="48207-130">Následující příkaz vytvoří volána sestavení zásady vydavatele `policy.1.0.myAssembly` ze souboru zásad vydavatele názvem `pub.config`, přiřadí silné název sestavení pomocí páru klíčů jako `sgKey.snk` souboru a určuje, že sestavení cílí x86 Architektura procesoru.</span><span class="sxs-lookup"><span data-stu-id="48207-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="48207-131">Sestavení zásady vydavatele musí odpovídat architektuře procesoru sestavení, které se vztahuje na.</span><span class="sxs-lookup"><span data-stu-id="48207-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="48207-132">Proto pokud má vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> hodnotu <xref:System.Reflection.ProcessorArchitecture.MSIL>, sestavení zásady vydavatele pro toto sestavení musí být vytvořeny s `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="48207-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="48207-133">Je nutné zadat samostatné sestavení zásady vydavatele pro každé sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="48207-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="48207-134">Důsledkem tohoto pravidla je, aby bylo možné změnit na architektuře procesoru pro sestavení, musíte změnit komponentu hlavních nebo vedlejších číslo verze, takže můžete zadat nové sestavení zásady vydavatele s správnou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="48207-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="48207-135">Původní sestavení zásady vydavatele nemůže obsloužit váš sestavení po vaší sestavení má jinou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="48207-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="48207-136">Jiné důsledkem je, že verze 2.0 linkeru nelze použít k vytvoření sestavení zásady vydavatele pro sestavení zkompilovaného pomocí starší verze rozhraní .NET Framework, protože vždy určuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="48207-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="48207-137">Přidání sestavení zásady vydavatele do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="48207-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="48207-138">Použití [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) sestavení zásady vydavatele přidat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="48207-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="48207-139">Sestavení zásady vydavatele přidat do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="48207-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="48207-140">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="48207-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="48207-141">**Gacutil /i***publisherPolicyAssemblyFile* </span><span class="sxs-lookup"><span data-stu-id="48207-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="48207-142">Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="48207-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="48207-143">Sestavení zásady vydavatele nelze přidat do globální mezipaměti sestavení, pokud se původní soubor zásad vydavatele nachází ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="48207-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48207-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="48207-144">See Also</span></span>  
 [<span data-ttu-id="48207-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="48207-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="48207-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="48207-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="48207-147">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="48207-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="48207-148">Konfigurace aplikací rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="48207-148">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="48207-149">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="48207-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="48207-150">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="48207-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="48207-151">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="48207-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
