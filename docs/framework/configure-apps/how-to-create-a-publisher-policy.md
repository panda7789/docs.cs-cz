---
title: 'Postupy: Vytváření zásad vydavatele'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646057"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="35595-102">Postupy: Vytváření zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="35595-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="35595-103">Dodavatelé sestavení mohou uvést, že aplikace by měly používat novější verzi sestavení zahrnutím souboru zásad vydavatele s upgradované sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="35595-104">Soubor zásad vydavatele určuje přesměrování sestavení a základní nastavení kódu a používá stejný formát jako konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="35595-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="35595-105">Soubor zásad vydavatele je zkompilován do sestavení a umístěn do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="35595-106">Při vytváření zásad vydavatele jsou zapojeny tři kroky:</span><span class="sxs-lookup"><span data-stu-id="35595-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="35595-107">Vytvořte soubor zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="35595-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="35595-108">Vytvořte sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="35595-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="35595-109">Přidejte sestavení zásad vydavatele do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="35595-110">Zásady schématu pro vydavatele jsou popsány v části [Přesměrovat verze sestavení](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="35595-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="35595-111">Následující příklad ukazuje soubor zásad vydavatele, který `myAssembly` přesměruje jednu verzi na jinou.</span><span class="sxs-lookup"><span data-stu-id="35595-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="35595-112">Informace o tom, jak zadat základ kódu, naleznete [v tématu Určení umístění sestavení](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="35595-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="35595-113">Vytvoření sestavení zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="35595-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="35595-114">Pomocí [propojovacího zařízení sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) vytvořte sestavení zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="35595-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="35595-115">Vytvoření sestavení zásad vydavatele</span><span class="sxs-lookup"><span data-stu-id="35595-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="35595-116">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="35595-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="35595-117">V tomto příkazu:</span><span class="sxs-lookup"><span data-stu-id="35595-117">In this command:</span></span>

- <span data-ttu-id="35595-118">Argument `publisherPolicyFile` je název souboru zásad vydavatele.</span><span class="sxs-lookup"><span data-stu-id="35595-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="35595-119">Argument `publisherPolicyAssemblyFile` je název sestavení zásad vydavatele, který je výsledkem tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="35595-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="35595-120">Název souboru sestavení musí následovat podle formátu:</span><span class="sxs-lookup"><span data-stu-id="35595-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="35595-121">'policy.majorNumber.minorNumber.mainAssemblyName.dll'</span><span class="sxs-lookup"><span data-stu-id="35595-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="35595-122">Argument `keyPairFile` je název souboru obsahujícího dvojici klíčů.</span><span class="sxs-lookup"><span data-stu-id="35595-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="35595-123">Sestavení sestavení a sestavení zásad vydavatele je nutné podepsat se stejným párem klíčů.</span><span class="sxs-lookup"><span data-stu-id="35595-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="35595-124">Argument `processorArchitecture` identifikuje platformu, na kterou cílí sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="35595-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="35595-125">Možnost cílit na konkrétní architekturu procesoru je k dispozici počínaje rozhraním .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="35595-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="35595-126">Možnost cílit na konkrétní architekturu procesoru je k dispozici počínaje rozhraním .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="35595-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="35595-127">Následující příkaz vytvoří sestavení zásad `policy.1.0.myAssembly` vydavatele volané `pub.config`ze souboru zásad vydavatele s názvem `sgKey.snk` , přiřadí sestavení silný název pomocí dvojice klíčů v souboru a určí, že sestavení cílí na architekturu procesoru x86.</span><span class="sxs-lookup"><span data-stu-id="35595-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="35595-128">Sestavení zásad vydavatele musí odpovídat architektuře procesoru sestavení, na které se vztahuje.</span><span class="sxs-lookup"><span data-stu-id="35595-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="35595-129">Proto pokud vaše sestavení <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> má <xref:System.Reflection.ProcessorArchitecture.MSIL>hodnotu , sestavení zásad vydavatele `/platform:anycpu`pro toto sestavení musí být vytvořeny s .</span><span class="sxs-lookup"><span data-stu-id="35595-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="35595-130">Je nutné zadat samostatné sestavení zásad vydavatele pro každé sestavení specifické pro procesor.</span><span class="sxs-lookup"><span data-stu-id="35595-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="35595-131">Důsledkem tohoto pravidla je, že chcete-li změnit architekturu procesoru pro sestavení, je nutné změnit hlavní nebo menší součást čísla verze, abyste mohli zadat nové sestavení zásad vydavatele se správnou architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="35595-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="35595-132">Staré sestavení zásad vydavatele nemůže obsluhovat vaše sestavení, jakmile má vaše sestavení jinou architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="35595-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="35595-133">Dalším důsledkem je, že propojovací program verze 2.0 nelze použít k vytvoření sestavení zásad vydavatele pro sestavení zkompilované pomocí dřívějších verzí rozhraní .NET Framework, protože vždy určuje architekturu procesoru.</span><span class="sxs-lookup"><span data-stu-id="35595-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="35595-134">Přidání sestavení zásad vydavatele do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="35595-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="35595-135">Pomocí [nástroje Globální mezipaměti sestavení (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) přidejte sestavení zásad vydavatele do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="35595-136">Přidání sestavení zásad vydavatele do globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="35595-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="35595-137">Na příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="35595-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="35595-138">Následující příkaz `policy.1.0.myAssembly.dll` přidá do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="35595-139">Sestavení zásad vydavatele nelze přidat do globální mezipaměti sestavení, `/link` pokud původní soubor zásad vydavatele zadaný v argumentu není umístěn ve stejném adresáři jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="35595-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="35595-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="35595-140">See also</span></span>

- [<span data-ttu-id="35595-141">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="35595-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="35595-142">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="35595-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="35595-143">Konfigurace aplikací pomocí konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="35595-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="35595-144">Schéma nastavení běhu</span><span class="sxs-lookup"><span data-stu-id="35595-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="35595-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="35595-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="35595-146">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="35595-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
