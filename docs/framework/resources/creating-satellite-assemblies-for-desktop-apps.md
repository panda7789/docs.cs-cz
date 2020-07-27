---
title: Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
description: Začněte vytvářet satelitní sestavení pro aplikace klasické pracovní plochy. Satelitní sestavení může být snadno Aktualizováno nebo nahrazeno k poskytnutí lokalizovaných prostředků.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
ms.openlocfilehash: be6603f3a593d9756d55204024214660b2220af3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166218"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="9c68b-104">Vytváření satelitních sestavení pro aplikace klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="9c68b-104">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="9c68b-105">Soubory prostředků hrají ústřední roli v lokalizovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="9c68b-105">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="9c68b-106">Umožňují aplikaci zobrazovat řetězce, obrázky a další data v jazyce a jazykové verzi uživatele a poskytovat alternativní data v případě, že prostředky pro vlastní jazyk nebo jazykovou verzi uživatele nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9c68b-106">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="9c68b-107">.NET Framework používá model hvězdicové a hvězdicové k vyhledání a načtení lokalizovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c68b-107">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="9c68b-108">Centrum je hlavní sestavení, které obsahuje nelokalizovatelný spustitelný kód a prostředky pro jednu jazykovou verzi, která se nazývá neutrální nebo výchozí jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-108">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="9c68b-109">Výchozí jazyková verze je záložní jazyková verze pro aplikaci. používá se, když nejsou k dispozici žádné lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="9c68b-109">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="9c68b-110">Použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut k určení jazykové verze výchozí jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c68b-110">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="9c68b-111">Každý paprsek se připojuje k satelitnímu sestavení, které obsahuje prostředky pro jednu lokalizovanou jazykovou verzi, ale neobsahuje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="9c68b-111">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="9c68b-112">Vzhledem k tomu, že satelitní sestavení nejsou součástí hlavního sestavení, můžete snadno aktualizovat nebo nahradit prostředky, které odpovídají konkrétní jazykové verzi, aniž by bylo nutné nahradit hlavní sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c68b-112">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="9c68b-113">Prostředky výchozí jazykové verze aplikace mohou být také uloženy v satelitním sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-113">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="9c68b-114">K tomu přiřadíte <xref:System.Resources.NeutralResourcesLanguageAttribute> hodnotu atributu <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9c68b-114">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="9c68b-115">Název a umístění satelitního sestavení</span><span class="sxs-lookup"><span data-stu-id="9c68b-115">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="9c68b-116">Model hvězdicové lokality vyžaduje umístění prostředků do konkrétních umístění, aby je bylo možné snadno vyhledat a použít.</span><span class="sxs-lookup"><span data-stu-id="9c68b-116">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="9c68b-117">Pokud nezkompilujete a pojmenujte prostředky podle očekávání nebo pokud je neumístíte do správných umístění, modul CLR (Common Language Runtime) je nebude moci vyhledat a bude místo toho používat prostředky výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-117">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="9c68b-118">.NET Framework Správce prostředků reprezentované <xref:System.Resources.ResourceManager> objektem, slouží k automatickému přístupu k lokalizovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="9c68b-118">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="9c68b-119">Správce prostředků vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="9c68b-119">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="9c68b-120">Jedno satelitní sestavení musí zahrnovat všechny prostředky pro konkrétní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-120">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="9c68b-121">Jinými slovy, je třeba zkompilovat více souborů *. txt* nebo *. resx* do jednoho binárního souboru *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-121">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="9c68b-122">V adresáři aplikace musí být samostatný podadresář pro každou lokalizovanou jazykovou verzi, která ukládá prostředky této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-122">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="9c68b-123">Název podadresáře musí být stejný jako název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-123">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="9c68b-124">Alternativně můžete uložit satelitní sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9c68b-124">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="9c68b-125">V tomto případě musí součást informací o jazykové verzi silného názvu sestavení uvádět svou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-125">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="9c68b-126">(Další informace najdete v části [instalace satelitních sestavení v globální mezipaměti sestavení (GAC](#SN) ) dále v tomto tématu.)</span><span class="sxs-lookup"><span data-stu-id="9c68b-126">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="9c68b-127">Pokud vaše aplikace obsahuje prostředky pro subjazykové verze, umístěte každou podjazykovou verzi do samostatného podadresáře v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c68b-127">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="9c68b-128">Neumísťujte subjazykové verze v podadresářích do adresáře hlavní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-128">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="9c68b-129">Satelitní sestavení musí mít stejný název jako aplikace a musí používat příponu názvu souboru .resources.dll.</span><span class="sxs-lookup"><span data-stu-id="9c68b-129">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="9c68b-130">Například pokud má aplikace název *Example.exe*, musí být název každého satelitního sestavení *Example.resources.dll*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-130">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="9c68b-131">Všimněte si, že název satelitního sestavení neoznačuje jazykovou verzi svých souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c68b-131">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="9c68b-132">Satelitní sestavení se však zobrazí v adresáři, který určuje jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-132">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="9c68b-133">Informace o jazykové verzi satelitního sestavení musí být zahrnuty v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-133">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="9c68b-134">Chcete-li uložit název jazykové verze v metadatech satelitního sestavení, zadáte `/culture` možnost při použití [linkeru sestavení](../tools/al-exe-assembly-linker.md) pro vložení prostředků do satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-134">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="9c68b-135">Následující ilustrace znázorňuje ukázkovou adresářovou strukturu a požadavky na umístění pro aplikace, které neinstalujete do [globální mezipaměti sestavení (GAC](../app-domains/gac.md)).</span><span class="sxs-lookup"><span data-stu-id="9c68b-135">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="9c68b-136">Položky s příponami. txt a. Resources nebudou dodávány s konečnou aplikací.</span><span class="sxs-lookup"><span data-stu-id="9c68b-136">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="9c68b-137">Jedná se o mezilehlé soubory prostředků, které slouží k vytváření finálních sestavení satelitních prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c68b-137">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="9c68b-138">V tomto příkladu můžete nahradit soubory. resx pro soubory. txt.</span><span class="sxs-lookup"><span data-stu-id="9c68b-138">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="9c68b-139">Další informace najdete v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-139">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="9c68b-140">Následující obrázek ukazuje adresář satelitního sestavení:</span><span class="sxs-lookup"><span data-stu-id="9c68b-140">The following image shows the satellite assembly directory:</span></span>

![Adresář satelitního sestavení s lokalizovanými podadresáři kultur.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="9c68b-142">Kompilování satelitních sestavení</span><span class="sxs-lookup"><span data-stu-id="9c68b-142">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="9c68b-143">K kompilování textových souborů nebo souborů XML (*. resx*), které obsahují prostředky do binárních souborů *. Resources* , slouží [generátor souboru prostředků (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="9c68b-143">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="9c68b-144">Pak použijete [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) k zkompilování souborů *. Resources* do satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-144">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="9c68b-145">*Al.exe* vytvoří sestavení ze souborů *. Resources* , které zadáte.</span><span class="sxs-lookup"><span data-stu-id="9c68b-145">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="9c68b-146">Satelitní sestavení mohou obsahovat pouze prostředky; nemohou obsahovat žádný spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="9c68b-146">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="9c68b-147">Následující *Al.exe* příkaz vytvoří satelitní sestavení pro aplikaci `Example` z německých souborů řetězců Resources *. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-147">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="9c68b-148">Následující příkaz *Al.exe* také vytvoří satelitní sestavení pro aplikaci `Example` ze souborů *strings. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-148">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="9c68b-149">Možnost **/template** způsobí, že satelitní sestavení zdědí všechna metadata sestavení s výjimkou jeho informací o jazykové verzi z nadřazeného sestavení (*Example.dll*).</span><span class="sxs-lookup"><span data-stu-id="9c68b-149">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="9c68b-150">V následující tabulce jsou popsány možnosti *Al.exe* používané v těchto příkazech podrobněji:</span><span class="sxs-lookup"><span data-stu-id="9c68b-150">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="9c68b-151">Možnost</span><span class="sxs-lookup"><span data-stu-id="9c68b-151">Option</span></span>|<span data-ttu-id="9c68b-152">Popis</span><span class="sxs-lookup"><span data-stu-id="9c68b-152">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="9c68b-153">Určuje, že satelitní sestavení je zkompilováno do souboru knihovny (. dll).</span><span class="sxs-lookup"><span data-stu-id="9c68b-153">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="9c68b-154">Vzhledem k tomu, že satelitní sestavení neobsahuje spustitelný kód a není hlavním sestavením aplikace, je nutné uložit satelitní sestavení jako knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="9c68b-154">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="9c68b-155">Určuje název souboru prostředků, který se má vložit, když *Al.exe* zkompiluje sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-155">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="9c68b-156">Do satelitního sestavení můžete vložit více souborů. Resources, ale pokud používáte model hvězdicového a hvězdicového modelu, je nutné pro každou jazykovou verzi zkompilovat jedno satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="9c68b-157">Můžete však vytvořit samostatné soubory. Resources pro řetězce a objekty.</span><span class="sxs-lookup"><span data-stu-id="9c68b-157">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="9c68b-158">Určuje jazykovou verzi prostředku, který má být zkompilován.</span><span class="sxs-lookup"><span data-stu-id="9c68b-158">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="9c68b-159">Modul CLR (Common Language Runtime) používá tyto informace při hledání prostředků pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-159">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="9c68b-160">Pokud tuto možnost vynecháte, bude *Al.exe* stále kompilovat prostředek, ale modul runtime ho nebude moci najít, když si ho uživatel požádá.</span><span class="sxs-lookup"><span data-stu-id="9c68b-160">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="9c68b-161">Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="9c68b-161">Specifies the name of the output file.</span></span> <span data-ttu-id="9c68b-162">Název musí následovat po názvech standard *Base*. Resources. *přípona*, kde je *základem* název hlavního sestavení a *přípona* je platná přípona názvu souboru (například. dll).</span><span class="sxs-lookup"><span data-stu-id="9c68b-162">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="9c68b-163">Všimněte si, že modul runtime nemůže určit jazykovou verzi satelitního sestavení na základě názvu jeho výstupního souboru; k určení je nutné použít možnost **/culture** .</span><span class="sxs-lookup"><span data-stu-id="9c68b-163">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="9c68b-164">Určuje sestavení, ze kterého bude satelitní sestavení dědit všechna metadata sestavení kromě pole culture.</span><span class="sxs-lookup"><span data-stu-id="9c68b-164">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="9c68b-165">Tato možnost ovlivňuje satelitní sestavení pouze v případě, že zadáte sestavení se [silným názvem](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-165">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="9c68b-166">Úplný seznam možností, které jsou k dispozici v *Al.exe*, naleznete v tématu [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-166">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="9c68b-167">Satelitní sestavení: příklad</span><span class="sxs-lookup"><span data-stu-id="9c68b-167">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="9c68b-168">Následuje jednoduchý příklad "Hello World", který zobrazuje okno se zprávou obsahující lokalizovaný pozdrav.</span><span class="sxs-lookup"><span data-stu-id="9c68b-168">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="9c68b-169">Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie) a ruština (Rusko) a její záložní jazyková verze je angličtina.</span><span class="sxs-lookup"><span data-stu-id="9c68b-169">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="9c68b-170">Chcete-li vytvořit příklad, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="9c68b-170">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="9c68b-171">Vytvořte soubor prostředků s názvem *Greetings. resx* nebo *Greeting.txt* , který bude obsahovat prostředek pro výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-171">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="9c68b-172">Uloží jeden řetězec s názvem, `HelloString` jehož hodnota je Hello World!.</span><span class="sxs-lookup"><span data-stu-id="9c68b-172">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="9c68b-173">v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="9c68b-173">in this file.</span></span>

2. <span data-ttu-id="9c68b-174">Chcete-li označit, že angličtina (EN) je výchozí jazyková verze aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c68b-174">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. <span data-ttu-id="9c68b-175">Přidejte podporu pro další jazykové verze (EN-US, fr-FR a ru-RU) do aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9c68b-175">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="9c68b-176">Pro podporu jazykové verze en-US nebo angličtiny (USA) vytvořte soubor prostředků s názvem *Greetings. en-US. resx* nebo *Greeting.en-US.txt*a uložte ho do něj s jedním řetězcem s názvem `HelloString` "Hi World!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-176">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="9c68b-177">Pro podporu jazykové verze fr-FR nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *Greeting.fr-fr. resx* nebo *Greeting.fr-FR.txt*a uložte ho do něj s jediným řetězcem, `HelloString` jehož hodnota je "Salut tout Le Monde!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-177">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="9c68b-178">Pro podporu jazykové verze ru-RU nebo ruštiny (Rusko) vytvořte soubor prostředků s názvem *Greeting.ru-ru. resx* nebo *Greeting.ru-RU.txt*a uložte ho do něj s jediným řetězcem s názvem `HelloString` "Всем привет!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-178">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="9c68b-179">Použijte [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) ke kompilaci každého textového souboru nebo souboru prostředků XML do binárního souboru *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-179">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="9c68b-180">Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-180">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="9c68b-181">Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="9c68b-181">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="9c68b-182">Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkazy pro zkompilování souborů *. resx* do souborů *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="9c68b-182">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="9c68b-183">Pokud jsou vaše prostředky v textových souborech namísto souborů XML, nahraďte příponu *. resx* textem *. txt*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-183">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="9c68b-184">Zkompilujte následující zdrojový kód spolu s prostředky pro výchozí jazykovou verzi do hlavního sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="9c68b-184">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9c68b-185">Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání <xref:System.Resources.ResourceManager> konstruktoru třídy na následující:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="9c68b-185">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="9c68b-186">Pokud je aplikace pojmenována jako příklad a kompilujete z příkazového řádku, příkaz pro kompilátor jazyka C# je:</span><span class="sxs-lookup"><span data-stu-id="9c68b-186">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="9c68b-187">Odpovídající příkaz kompilátoru Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9c68b-187">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="9c68b-188">Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="9c68b-188">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="9c68b-189">Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-189">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="9c68b-190">Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="9c68b-190">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="9c68b-191">Do satelitních sestavení vložte jednotlivé soubory *. Resources* specifické pro jazykovou verzi a uložte je do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="9c68b-191">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="9c68b-192">Příkaz k tomuto účelu pro každý soubor *. Resources* je:</span><span class="sxs-lookup"><span data-stu-id="9c68b-192">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="9c68b-193">kde *culture* je název jazykové verze, jejíž prostředky obsahuje satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-193">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="9c68b-194">Visual Studio zpracovává tento proces automaticky.</span><span class="sxs-lookup"><span data-stu-id="9c68b-194">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="9c68b-195">Pak můžete spustit příklad.</span><span class="sxs-lookup"><span data-stu-id="9c68b-195">You can then run the example.</span></span> <span data-ttu-id="9c68b-196">Bude náhodně vydávat jednu z podporovaných kultur aktuální jazykové verzi a zobrazí lokalizovaný pozdrav.</span><span class="sxs-lookup"><span data-stu-id="9c68b-196">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="9c68b-197">Instalace satelitních sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="9c68b-197">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="9c68b-198">Namísto instalace sestavení v podadresáři místní aplikace je můžete nainstalovat do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9c68b-198">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="9c68b-199">To je zvlášť užitečné, pokud máte knihovny tříd a sestavení prostředků knihovny tříd, které jsou používány více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-199">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="9c68b-200">Instalace sestavení do globální mezipaměti sestavení vyžaduje, aby měly silné názvy.</span><span class="sxs-lookup"><span data-stu-id="9c68b-200">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="9c68b-201">Sestavení se silným názvem jsou podepsaná s platnou dvojicí veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c68b-201">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="9c68b-202">Obsahují informace o verzi, kterou modul runtime používá k určení sestavení, které se má použít pro splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="9c68b-202">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="9c68b-203">Další informace o silných názvech a verzích najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-203">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="9c68b-204">Další informace o silných názvech naleznete v tématu [sestavení se silným názvem](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-204">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="9c68b-205">Při vývoji aplikace je nepravděpodobné, že budete mít přístup k finálnímu páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c68b-205">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="9c68b-206">Chcete-li nainstalovat satelitní sestavení v globální mezipaměti sestavení (GAC) a zajistit, že funguje podle očekávání, můžete použít techniku nazvanou zpožděné podepisování.</span><span class="sxs-lookup"><span data-stu-id="9c68b-206">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="9c68b-207">Při zpoždění podepsání sestavení v okamžiku sestavení rezervujete místo v souboru pro podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="9c68b-207">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="9c68b-208">Vlastní podepisování je zpožděné až později, až bude dostupný poslední pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c68b-208">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="9c68b-209">Další informace o zpožděném podepisování naleznete v tématu [Delay Signing Assembly](../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-209">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="9c68b-210">Získání veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="9c68b-210">Obtaining the Public Key</span></span>

<span data-ttu-id="9c68b-211">Chcete-li zpozdit podepsání sestavení, je nutné mít přístup k veřejnému klíči.</span><span class="sxs-lookup"><span data-stu-id="9c68b-211">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="9c68b-212">Můžete buď získat skutečný veřejný klíč z organizace ve vaší společnosti, který provede případné podepisování, nebo vytvořit veřejný klíč pomocí [Nástroje pro silný název (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-212">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="9c68b-213">Následující *Sn.exe* příkaz vytvoří pár veřejného a privátního klíče testu.</span><span class="sxs-lookup"><span data-stu-id="9c68b-213">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="9c68b-214">Možnost **– k** určuje, že *Sn.exe* by měl vytvořit nový pár klíčů a uložit ho do souboru s názvem *TestKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-214">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="9c68b-215">Veřejný klíč můžete extrahovat ze souboru, který obsahuje pár testovacích klíčů.</span><span class="sxs-lookup"><span data-stu-id="9c68b-215">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="9c68b-216">Následující příkaz extrahuje veřejný klíč z *TestKeyPair. snk* a uloží jej do *PublicKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="9c68b-216">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="9c68b-217">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="9c68b-217">Delay Signing an Assembly</span></span>

<span data-ttu-id="9c68b-218">Po získání nebo vytvoření veřejného klíče použijete [linker sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) pro zkompilování sestavení a zadáte zpožděné podepisování.</span><span class="sxs-lookup"><span data-stu-id="9c68b-218">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="9c68b-219">Následující *Al.exe* příkaz vytvoří satelitní sestavení se silným názvem pro aplikaci StringLibrary ze souboru *strings. ja. Resources* :</span><span class="sxs-lookup"><span data-stu-id="9c68b-219">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="9c68b-220">Možnost **-Delay +** určuje, že linker sestavení by měl zpozdit podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-220">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="9c68b-221">Možnost **-keyfile** Určuje název souboru klíče, který obsahuje veřejný klíč, který se použije pro Zpožděné podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-221">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="9c68b-222">Opětovné podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="9c68b-222">Re-signing an Assembly</span></span>

<span data-ttu-id="9c68b-223">Před nasazením aplikace je nutné znovu podepsat zpožděné satelitní sestavení se skutečným párem klíčů.</span><span class="sxs-lookup"><span data-stu-id="9c68b-223">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="9c68b-224">To můžete provést pomocí *Sn.exe*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-224">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="9c68b-225">Následující příkaz *Sn.exe* podepíše *StringLibrary.resources.dll* dvojici klíčů uloženou v souboru *RealKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-225">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="9c68b-226">Možnost **– R** určuje, že dříve podepsané nebo zpožděné podepsané sestavení má být znovu podepsáno.</span><span class="sxs-lookup"><span data-stu-id="9c68b-226">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="9c68b-227">Instalace satelitního sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="9c68b-227">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="9c68b-228">Pokud modul runtime vyhledává prostředky v záložním procesu prostředků, hledá nejprve [globální mezipaměť sestavení (GAC](../app-domains/gac.md) ).</span><span class="sxs-lookup"><span data-stu-id="9c68b-228">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="9c68b-229">(Další informace najdete v části "proces záložního prostředku" v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md) .) Jakmile je satelitní sestavení podepsáno silným názvem, lze jej nainstalovat do globální mezipaměti sestavení [(GAC) pomocí nástroj Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="9c68b-229">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="9c68b-230">Následující *Gacutil.exe* příkaz nainstaluje *StringLibrary.resources.dll*\* v globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="9c68b-230">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="9c68b-231">Možnost **/i** určuje, že *Gacutil.exe* by měl nainstalovat zadané sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9c68b-231">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="9c68b-232">Po instalaci satelitního sestavení v mezipaměti budou prostředky, které obsahuje, zpřístupněny všem aplikacím, které jsou navrženy pro použití satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-232">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="9c68b-233">Prostředky v globální mezipaměti sestavení (GAC): příklad</span><span class="sxs-lookup"><span data-stu-id="9c68b-233">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="9c68b-234">Následující příklad používá metodu v knihovně tříd .NET Framework k extrakci a vrácení lokalizovaného pozdravu ze souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="9c68b-234">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="9c68b-235">Knihovna a její prostředky jsou registrovány v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9c68b-235">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="9c68b-236">Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie), ruština (Rusko) a anglické kultury.</span><span class="sxs-lookup"><span data-stu-id="9c68b-236">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="9c68b-237">Výchozí jazyková verze je angličtina; jeho prostředky jsou uloženy v hlavním sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-237">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="9c68b-238">Příklad prvotního zpoždění podepíše knihovnu a její satelitní sestavení pomocí veřejného klíče a pak je znovu podepíše s párem veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c68b-238">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="9c68b-239">Chcete-li vytvořit příklad, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="9c68b-239">To create the example, do the following:</span></span>

1. <span data-ttu-id="9c68b-240">Pokud nepoužíváte aplikaci Visual Studio, použijte následující příkaz se [silným názvem (Sn.exe)](../tools/sn-exe-strong-name-tool.md) a vytvořte dvojici veřejného a privátního klíče s názvem *ResKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="9c68b-240">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="9c68b-241">Pokud používáte sadu Visual Studio, použijte k vygenerování souboru klíče kartu **podepisování** v dialogovém okně **vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="9c68b-241">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="9c68b-242">K vytvoření souboru veřejného klíče s názvem *PublicKey. snk*použijte následující příkaz [nástroje se silným názvem (Sn.exe)](../tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="9c68b-242">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="9c68b-243">Vytvořte soubor prostředků s názvem *strings. resx* , který bude obsahovat prostředek pro výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="9c68b-243">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="9c68b-244">Uložte jeden řetězec s názvem `Greeting` , jehož hodnota je "jak provést?"</span><span class="sxs-lookup"><span data-stu-id="9c68b-244">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="9c68b-245">v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="9c68b-245">in that file.</span></span>

4. <span data-ttu-id="9c68b-246">Chcete-li označit, že "en" je výchozí jazykovou verzí aplikace, přidejte následující <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="9c68b-246">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="9c68b-247">Přidejte podporu pro další jazykové verze (kultury en-US, fr-FR a ru-RU) do aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9c68b-247">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="9c68b-248">Chcete-li podporovat jazykovou verzi "en-US" nebo anglickou (USA), vytvořte soubor prostředků s názvem *strings. en-US. resx* nebo *Strings.en-US.txt*a uložte jej do něj jediným řetězcem, `Greeting` jehož hodnota je "Hello!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-248">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="9c68b-249">Pro podporu jazykové verze fr-FR nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *strings.fr-fr. resx* nebo *Strings.fr-FR.txt* a uložte ho do něj s jedním řetězcem s názvem `Greeting` "šťastného jour!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-249">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="9c68b-250">Pro podporu "ru-RU" nebo ruské jazykové verze (Rusko) vytvořte soubor prostředků s názvem *strings.ru-ru. resx* nebo *Strings.ru-RU.txt* a uložte do něj jediný řetězec s názvem, `Greeting` jehož hodnota je "привет!".</span><span class="sxs-lookup"><span data-stu-id="9c68b-250">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="9c68b-251">Použijte [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) ke kompilaci každého textového souboru nebo souboru prostředků XML do binárního souboru. Resources.</span><span class="sxs-lookup"><span data-stu-id="9c68b-251">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="9c68b-252">Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-252">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="9c68b-253">Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="9c68b-253">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="9c68b-254">Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkaz pro zkompilování souborů *. resx* do souborů *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="9c68b-254">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="9c68b-255">Kde *filename* je volitelná cesta, název souboru a Přípona souboru *. resx* nebo textového souboru.</span><span class="sxs-lookup"><span data-stu-id="9c68b-255">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="9c68b-256">Zkompilujte následující zdrojový kód pro *StringLibrary. vb* nebo *StringLibrary.cs* spolu s prostředky pro výchozí jazykovou verzi do zpožděně podepsaného sestavení knihovny s názvem *StringLibrary.dll*:</span><span class="sxs-lookup"><span data-stu-id="9c68b-256">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9c68b-257">Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání <xref:System.Resources.ResourceManager> konstruktoru třídy na `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);` .</span><span class="sxs-lookup"><span data-stu-id="9c68b-257">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="9c68b-258">Příkaz pro kompilátor jazyka C# je:</span><span class="sxs-lookup"><span data-stu-id="9c68b-258">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="9c68b-259">Odpovídající příkaz kompilátoru Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9c68b-259">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="9c68b-260">Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="9c68b-260">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="9c68b-261">Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="9c68b-261">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="9c68b-262">Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="9c68b-262">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="9c68b-263">Vzhledem k tomu, že všechna satelitní sestavení mají stejný název souboru, podadresáře se používají k ukládání jednotlivých satelitních sestavení specifických pro jazykovou verzi, dokud nejsou podepsány pomocí páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="9c68b-263">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="9c68b-264">Vložte jednotlivé soubory *prostředků* specifické pro jazykovou verzi do zpožděně podepsaných satelitních sestavení a uložte je do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="9c68b-264">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="9c68b-265">Příkaz k tomuto účelu pro každý soubor *. Resources* je:</span><span class="sxs-lookup"><span data-stu-id="9c68b-265">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="9c68b-266">kde *culture* je název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c68b-266">where *culture* is the name of a culture.</span></span> <span data-ttu-id="9c68b-267">V tomto příkladu jsou názvy jazykové verze en-US, fr-FR a ru-RU.</span><span class="sxs-lookup"><span data-stu-id="9c68b-267">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="9c68b-268">Znovu podepište *StringLibrary.dll* pomocí [nástroje Strong Name (Sn.exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9c68b-268">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="9c68b-269">Znovu podepište jednotlivá satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c68b-269">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="9c68b-270">Chcete-li to provést, použijte [Nástroj silného názvu (Sn.exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem pro každé satelitní sestavení:</span><span class="sxs-lookup"><span data-stu-id="9c68b-270">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="9c68b-271">Pomocí následujícího příkazu zaregistrujte *StringLibrary.dll* a každého ze svých satelitních sestavení v globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="9c68b-271">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="9c68b-272">kde *filename* je název souboru, který se má zaregistrovat.</span><span class="sxs-lookup"><span data-stu-id="9c68b-272">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="9c68b-273">Pokud používáte aplikaci Visual Studio, vytvořte nový projekt **konzolové aplikace** s názvem `Example` , přidejte odkaz na *StringLibrary.dll* a následující zdrojový kód a zkompilujte.</span><span class="sxs-lookup"><span data-stu-id="9c68b-273">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="9c68b-274">Pro zkompilování z příkazového řádku, použijte následující příkaz pro kompilátor jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="9c68b-274">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="9c68b-275">Příkazový řádek pro kompilátor Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="9c68b-275">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="9c68b-276">Spusťte *Example.exe*.</span><span class="sxs-lookup"><span data-stu-id="9c68b-276">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c68b-277">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c68b-277">See also</span></span>

- [<span data-ttu-id="9c68b-278">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="9c68b-278">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="9c68b-279">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="9c68b-279">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="9c68b-280">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="9c68b-280">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="9c68b-281">Sn.exe (Nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="9c68b-281">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="9c68b-282">Gacutil.exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="9c68b-282">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="9c68b-283">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="9c68b-283">Resources in Desktop Apps</span></span>](index.md)
