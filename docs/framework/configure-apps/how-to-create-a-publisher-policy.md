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
ms.openlocfilehash: 3969f066c0a17424d2c4527d2b4661b30f5bb6d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530522"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="b61a1-102">Postupy: Vytváření zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="b61a1-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="b61a1-103">Dodavatelé sestavení mohou stavu, že aplikace by měly používat novější verze sestavení zahrnutím souboru zásad vydavatele s upgradovaný sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="b61a1-104">Soubor zásad vydavatele, který určuje přesměrování sestavení a nastavení základní kód a používá stejný formát jako konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="b61a1-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="b61a1-105">Soubor zásad vydavatele, který je zkompilován sestavení a umístěn v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="b61a1-106">Při vytváření zásad vydavatele jsou tři kroky:</span><span class="sxs-lookup"><span data-stu-id="b61a1-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="b61a1-107">Vytvořte soubor zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b61a1-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="b61a1-108">Vytvořte sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b61a1-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="b61a1-109">Přidáte sestavení zásad vydavatele do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="b61a1-110">Schéma pro zásady vydavatele je popsána v [přesměrování verze sestavení](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b61a1-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="b61a1-111">Následující příklad ukazuje vydavatele souboru zásad, který přesměruje jednu verzi `myAssembly` do jiného.</span><span class="sxs-lookup"><span data-stu-id="b61a1-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
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
  
 <span data-ttu-id="b61a1-112">Zjistěte, jak určit základ kódu, naleznete v tématu [určení umístění sestavení](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="b61a1-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="b61a1-113">Vytváření sestavení zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="b61a1-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="b61a1-114">Použití [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) k vytvoření sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b61a1-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="b61a1-115">Chcete-li vytvořit sestavení zásady vydavatele</span><span class="sxs-lookup"><span data-stu-id="b61a1-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="b61a1-116">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b61a1-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="b61a1-117">**Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="b61a1-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="b61a1-118">V tomto příkazu:</span><span class="sxs-lookup"><span data-stu-id="b61a1-118">In this command:</span></span>  
  
    -   <span data-ttu-id="b61a1-119">*PublisherPolicyFile* argumentem je název souboru zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="b61a1-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="b61a1-120">*PublisherPolicyAssemblyFile* argumentem je název sestavení zásad vydavatele, která je výsledkem tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="b61a1-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="b61a1-121">Název souboru sestavení musí vyhovovat formátu:</span><span class="sxs-lookup"><span data-stu-id="b61a1-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="b61a1-122">**policy.**</span><span class="sxs-lookup"><span data-stu-id="b61a1-122">**policy.**</span></span> <span data-ttu-id="b61a1-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="b61a1-123">*majorNumber* **.**</span></span> <span data-ttu-id="b61a1-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="b61a1-124">*minorNumber* **.**</span></span> <span data-ttu-id="b61a1-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="b61a1-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="b61a1-126">*KeyPairFile* argumentem je název souboru, který obsahuje pár klíčů.</span><span class="sxs-lookup"><span data-stu-id="b61a1-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="b61a1-127">Musíte podepsat sestavení a sestavení zásad vydavatele s stejného páru klíčů.</span><span class="sxs-lookup"><span data-stu-id="b61a1-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="b61a1-128">*ProcessorArchitecture* argument určuje platformu cílem sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="b61a1-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="b61a1-129">Možnost Cílová architektura procesoru je v rozhraní .NET Framework verze 2.0 nový.</span><span class="sxs-lookup"><span data-stu-id="b61a1-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="b61a1-130">Následující příkaz vytvoří sestavení zásad vydavatele volá `policy.1.0.myAssembly` ze souboru zásad vydavatele volá `pub.config`, přiřadí silný název sestavení pomocí páru klíčů v `sgKey.snk` souboru a určí, že sestavení, zaměřuje x86 Architektura procesoru.</span><span class="sxs-lookup"><span data-stu-id="b61a1-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="b61a1-131">Sestavení zásad vydavatele musí odpovídat architektuře procesoru, který se vztahuje na sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="b61a1-132">Proto pokud vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> hodnotu <xref:System.Reflection.ProcessorArchitecture.MSIL>, sestavení zásady vydavatele pro toto sestavení je potřeba vytvořit s `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="b61a1-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="b61a1-133">Je nutné zadat samostatné sestavení zásady vydavatele pro každé sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="b61a1-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="b61a1-134">V důsledku tohoto pravidla je, že chcete-li změnit na architektuře procesoru pro sestavení, je nutné změnit hlavních nebo vedlejších součást čísla verze, tak, že zadáte nové sestavení zásad vydavatele s správnou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="b61a1-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="b61a1-135">Staré sestavení zásad vydavatele nelze služby sestavení, jakmile vaše sestavení obsahuje jinou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="b61a1-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="b61a1-136">Jiné důsledkem je, že má linker verze 2.0 nelze použít k vytvoření sestavení zásady vydavatele pro sestavení zkompilovaného pomocí starší verze rozhraní .NET Framework, protože vždycky určuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="b61a1-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="b61a1-137">Přidání sestavení zásad vydavatele do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="b61a1-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="b61a1-138">Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) přidání sestavení zásad vydavatele do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="b61a1-139">Přidání sestavení zásad vydavatele do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="b61a1-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="b61a1-140">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="b61a1-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="b61a1-141">\**Gacutil /i\*\*\*publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="b61a1-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="b61a1-142">Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b61a1-143">Sestavení zásad vydavatele nelze přidat do globální mezipaměti sestavení, pokud původní soubor zásad vydavatele se nachází ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="b61a1-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61a1-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b61a1-144">See also</span></span>
- [<span data-ttu-id="b61a1-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="b61a1-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="b61a1-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b61a1-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b61a1-147">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="b61a1-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="b61a1-148">Konfigurace aplikací .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b61a1-148">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [<span data-ttu-id="b61a1-149">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b61a1-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b61a1-150">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b61a1-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="b61a1-151">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="b61a1-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
