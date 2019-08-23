---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: bf5b55eb01a31106fcc7cb0d79212416ab0c898d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913050"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="9dcbd-102">Postupy: Vytváření zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="9dcbd-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="9dcbd-103">Dodavatelé sestavení mohou stanovit, že aplikace by měly používat novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradovaným sestavením.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="9dcbd-104">Soubor zásad vydavatele určuje přesměrování sestavení a základní nastavení kódu a používá stejný formát jako konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="9dcbd-105">Soubor zásad vydavatele je zkompilován do sestavení a umístěn do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9dcbd-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="9dcbd-106">Existují tři kroky, které se týkají vytváření zásad vydavatele:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1. <span data-ttu-id="9dcbd-107">Vytvořte soubor zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-107">Create a publisher policy file.</span></span>  
  
2. <span data-ttu-id="9dcbd-108">Vytvořte sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-108">Create a publisher policy assembly.</span></span>  
  
3. <span data-ttu-id="9dcbd-109">Přidejte sestavení zásad vydavatele do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9dcbd-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="9dcbd-110">Schéma pro zásady vydavatele je popsáno v tématu [Přesměrování verzí sestavení](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="9dcbd-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="9dcbd-111">Následující příklad ukazuje soubor zásad vydavatele, který přesměruje jednu verzi `myAssembly` na jinou.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
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
  
 <span data-ttu-id="9dcbd-112">Informace o tom, jak zadat základ kódu, naleznete v tématu [určení umístění sestavení](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="9dcbd-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="9dcbd-113">Vytváření sestavení zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="9dcbd-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="9dcbd-114">Pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md) vytvořte sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="9dcbd-115">Vytvoření sestavení zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="9dcbd-115">To create a publisher policy assembly</span></span>  
  
1. <span data-ttu-id="9dcbd-116">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="9dcbd-117">**Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/Platform:** *ProcessorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="9dcbd-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="9dcbd-118">V tomto příkazu:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-118">In this command:</span></span>  
  
    - <span data-ttu-id="9dcbd-119">Argument *publisherPolicyFile* je název souboru zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    - <span data-ttu-id="9dcbd-120">Argument *publisherPolicyAssemblyFile* je název sestavení zásad vydavatele, které je výsledkem tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="9dcbd-121">Název souboru sestavení musí odpovídat formátu:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="9dcbd-122">**politických.**</span><span class="sxs-lookup"><span data-stu-id="9dcbd-122">**policy.**</span></span> <span data-ttu-id="9dcbd-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="9dcbd-123">*majorNumber* **.**</span></span> <span data-ttu-id="9dcbd-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="9dcbd-124">*minorNumber* **.**</span></span> <span data-ttu-id="9dcbd-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="9dcbd-125">*mainAssemblyName* **.dll**</span></span>  
  
    - <span data-ttu-id="9dcbd-126">Argument *keyPairFile* je název souboru, který obsahuje dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="9dcbd-127">Sestavení zásad sestavení a vydavatel je nutné podepsat se stejnou dvojicí klíčů.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    - <span data-ttu-id="9dcbd-128">Argument *ProcessorArchitecture* identifikuje platformu, na kterou cílí sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="9dcbd-129">Možnost zaměřit se na konkrétní architekturu procesoru je nová verze .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="9dcbd-130">Následující příkaz vytvoří sestavení zásad vydavatele nazvané `policy.1.0.myAssembly` ze souboru zásad vydavatele s názvem `pub.config`, přiřadí sestavení silný název pomocí páru klíčů v `sgKey.snk` souboru a určí, že sestavení cílí na x86. Architektura procesoru.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="9dcbd-131">Sestavení zásad vydavatele se musí shodovat s architekturou procesoru sestavení, na které se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="9dcbd-132">Proto pokud má <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> vaše sestavení <xref:System.Reflection.ProcessorArchitecture.MSIL>hodnotu, musí být sestavení zásad vydavatele pro toto sestavení vytvořeno pomocí `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="9dcbd-133">Pro každé sestavení specifické pro procesor musíte zadat samostatné sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="9dcbd-134">V důsledku tohoto pravidla je, že pro změnu architektury procesoru pro sestavení je nutné změnit hlavní nebo dílčí komponentu čísla verze, abyste mohli dodat nové sestavení zásad vydavatele se správnou architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="9dcbd-135">Sestavení původní zásady vydavatele nemůže obsluhovat sestavení, jakmile má vaše sestavení jinou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="9dcbd-136">Další příčinou je, že linker verze 2,0 nelze použít k vytvoření sestavení zásad vydavatele pro sestavení zkompilované pomocí dřívější verze .NET Framework, protože vždy určuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="9dcbd-137">Přidání sestavení zásad vydavatele do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="9dcbd-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="9dcbd-138">K přidání sestavení zásad vydavatele do globální mezipaměti sestavení [(GAC) použijte nástroj Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="9dcbd-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="9dcbd-139">Chcete-li přidat sestavení zásad vydavatele do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="9dcbd-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1. <span data-ttu-id="9dcbd-140">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="9dcbd-141">**Gacutil /i** *publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="9dcbd-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="9dcbd-142">Následující příkaz přidá `policy.1.0.myAssembly.dll` do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9dcbd-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9dcbd-143">Sestavení zásady vydavatele nelze přidat do globální mezipaměti sestavení (GAC), pokud původní soubor zásad vydavatele není umístěn ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="9dcbd-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dcbd-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9dcbd-144">See also</span></span>

- [<span data-ttu-id="9dcbd-145">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="9dcbd-145">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="9dcbd-146">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="9dcbd-146">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9dcbd-147">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="9dcbd-147">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="9dcbd-148">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="9dcbd-148">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="9dcbd-149">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9dcbd-149">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="9dcbd-150">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="9dcbd-150">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
