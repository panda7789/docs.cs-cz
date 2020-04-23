---
title: Vytváření satelitních sestavení pro aplikace klasické pracovní plochy
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
ms.openlocfilehash: 5efc5001a1a9756e09053d684a2f6673d15fadcf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458016"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="21ce1-102">Vytváření satelitních sestavení pro aplikace klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="21ce1-102">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="21ce1-103">Soubory prostředků hrají ústřední roli v lokalizovaných aplikacích.</span><span class="sxs-lookup"><span data-stu-id="21ce1-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="21ce1-104">Umožňují aplikaci zobrazovat řetězce, obrázky a další data v jazyce a jazykové verzi uživatele a poskytovat alternativní data v případě, že prostředky pro vlastní jazyk nebo jazykovou verzi uživatele nejsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="21ce1-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="21ce1-105">.NET Framework používá model hvězdicové a hvězdicové k vyhledání a načtení lokalizovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="21ce1-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="21ce1-106">Centrum je hlavní sestavení, které obsahuje nelokalizovatelný spustitelný kód a prostředky pro jednu jazykovou verzi, která se nazývá neutrální nebo výchozí jazyková verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="21ce1-107">Výchozí jazyková verze je záložní jazyková verze pro aplikaci. používá se, když nejsou k dispozici žádné lokalizované prostředky.</span><span class="sxs-lookup"><span data-stu-id="21ce1-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="21ce1-108">Použijte <xref:System.Resources.NeutralResourcesLanguageAttribute> atribut k určení jazykové verze výchozí jazykové verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="21ce1-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="21ce1-109">Každý paprsek se připojuje k satelitnímu sestavení, které obsahuje prostředky pro jednu lokalizovanou jazykovou verzi, ale neobsahuje žádný kód.</span><span class="sxs-lookup"><span data-stu-id="21ce1-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="21ce1-110">Vzhledem k tomu, že satelitní sestavení nejsou součástí hlavního sestavení, můžete snadno aktualizovat nebo nahradit prostředky, které odpovídají konkrétní jazykové verzi, aniž by bylo nutné nahradit hlavní sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="21ce1-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="21ce1-111">Prostředky výchozí jazykové verze aplikace mohou být také uloženy v satelitním sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="21ce1-112">K tomu přiřadíte hodnotu <xref:System.Resources.NeutralResourcesLanguageAttribute> atributu. <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="21ce1-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="21ce1-113">Název a umístění satelitního sestavení</span><span class="sxs-lookup"><span data-stu-id="21ce1-113">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="21ce1-114">Model hvězdicové lokality vyžaduje umístění prostředků do konkrétních umístění, aby je bylo možné snadno vyhledat a použít.</span><span class="sxs-lookup"><span data-stu-id="21ce1-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="21ce1-115">Pokud nezkompilujete a pojmenujte prostředky podle očekávání nebo pokud je neumístíte do správných umístění, modul CLR (Common Language Runtime) je nebude moci vyhledat a bude místo toho používat prostředky výchozí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="21ce1-116">.NET Framework Správce prostředků reprezentované <xref:System.Resources.ResourceManager> objektem, slouží k automatickému přístupu k lokalizovaným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="21ce1-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="21ce1-117">Správce prostředků vyžaduje následující:</span><span class="sxs-lookup"><span data-stu-id="21ce1-117">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="21ce1-118">Jedno satelitní sestavení musí zahrnovat všechny prostředky pro konkrétní jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="21ce1-119">Jinými slovy, je třeba zkompilovat více souborů *. txt* nebo *. resx* do jednoho binárního souboru *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-119">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="21ce1-120">V adresáři aplikace musí být samostatný podadresář pro každou lokalizovanou jazykovou verzi, která ukládá prostředky této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="21ce1-121">Název podadresáře musí být stejný jako název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="21ce1-122">Alternativně můžete uložit satelitní sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="21ce1-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="21ce1-123">V tomto případě musí součást informací o jazykové verzi silného názvu sestavení uvádět svou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="21ce1-124">(Další informace najdete v části [instalace satelitních sestavení v globální mezipaměti sestavení (GAC](#SN) ) dále v tomto tématu.)</span><span class="sxs-lookup"><span data-stu-id="21ce1-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="21ce1-125">Pokud vaše aplikace obsahuje prostředky pro subjazykové verze, umístěte každou podjazykovou verzi do samostatného podadresáře v adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="21ce1-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="21ce1-126">Neumísťujte subjazykové verze v podadresářích do adresáře hlavní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="21ce1-127">Satelitní sestavení musí mít stejný název jako aplikace a musí používat příponu názvu souboru. Resources. dll.</span><span class="sxs-lookup"><span data-stu-id="21ce1-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="21ce1-128">Například pokud je aplikace pojmenována *example. exe*, název každého satelitního sestavení by měl být *example. Resources. dll*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-128">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="21ce1-129">Všimněte si, že název satelitního sestavení neoznačuje jazykovou verzi svých souborů prostředků.</span><span class="sxs-lookup"><span data-stu-id="21ce1-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="21ce1-130">Satelitní sestavení se však zobrazí v adresáři, který určuje jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="21ce1-131">Informace o jazykové verzi satelitního sestavení musí být zahrnuty v metadatech sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="21ce1-132">Chcete-li uložit název jazykové verze v metadatech satelitního sestavení, zadáte `/culture` možnost při použití [linkeru sestavení](../tools/al-exe-assembly-linker.md) pro vložení prostředků do satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="21ce1-133">Následující ilustrace znázorňuje ukázkovou adresářovou strukturu a požadavky na umístění pro aplikace, které neinstalujete do [globální mezipaměti sestavení (GAC](../app-domains/gac.md)).</span><span class="sxs-lookup"><span data-stu-id="21ce1-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="21ce1-134">Položky s příponami. txt a. Resources nebudou dodávány s konečnou aplikací.</span><span class="sxs-lookup"><span data-stu-id="21ce1-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="21ce1-135">Jedná se o mezilehlé soubory prostředků, které slouží k vytváření finálních sestavení satelitních prostředků.</span><span class="sxs-lookup"><span data-stu-id="21ce1-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="21ce1-136">V tomto příkladu můžete nahradit soubory. resx pro soubory. txt.</span><span class="sxs-lookup"><span data-stu-id="21ce1-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="21ce1-137">Další informace najdete v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-137">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="21ce1-138">Následující obrázek ukazuje adresář satelitního sestavení:</span><span class="sxs-lookup"><span data-stu-id="21ce1-138">The following image shows the satellite assembly directory:</span></span>

![Adresář satelitního sestavení s lokalizovanými podadresáři kultur.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="21ce1-140">Kompilování satelitních sestavení</span><span class="sxs-lookup"><span data-stu-id="21ce1-140">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="21ce1-141">Nástroj [Resource File Generator (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) slouží k kompilování textových souborů nebo souborů XML (*. resx*), které obsahují prostředky do binárních souborů *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-141">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="21ce1-142">Pak pomocí [linkeru sestavení (Al. exe)](../tools/al-exe-assembly-linker.md) zkompilujete soubory *. Resources* do satelitních sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-142">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="21ce1-143">*Al. exe* vytvoří sestavení ze souborů *. Resources* , které zadáte.</span><span class="sxs-lookup"><span data-stu-id="21ce1-143">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="21ce1-144">Satelitní sestavení mohou obsahovat pouze prostředky; nemohou obsahovat žádný spustitelný kód.</span><span class="sxs-lookup"><span data-stu-id="21ce1-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="21ce1-145">Následující příkaz *Al. exe* vytvoří satelitní sestavení pro aplikaci `Example` ze souborů řetězců německého zdroje *. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-145">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="21ce1-146">Následující příkaz *Al. exe* také vytvoří satelitní sestavení pro aplikaci `Example` ze souborů *strings. de. Resources*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-146">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="21ce1-147">Možnost **/template** způsobí, že satelitní sestavení zdědí všechna metadata sestavení s výjimkou jeho informací o jazykové verzi z nadřazeného sestavení (*example. dll*).</span><span class="sxs-lookup"><span data-stu-id="21ce1-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="21ce1-148">V následující tabulce jsou popsány možnosti nástroje *Al. exe* použité v těchto příkazech podrobněji:</span><span class="sxs-lookup"><span data-stu-id="21ce1-148">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="21ce1-149">Možnost</span><span class="sxs-lookup"><span data-stu-id="21ce1-149">Option</span></span>|<span data-ttu-id="21ce1-150">Popis</span><span class="sxs-lookup"><span data-stu-id="21ce1-150">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="21ce1-151">Určuje, že satelitní sestavení je zkompilováno do souboru knihovny (. dll).</span><span class="sxs-lookup"><span data-stu-id="21ce1-151">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="21ce1-152">Vzhledem k tomu, že satelitní sestavení neobsahuje spustitelný kód a není hlavním sestavením aplikace, je nutné uložit satelitní sestavení jako knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="21ce1-152">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="21ce1-153">Určuje název souboru prostředků, který má být vložen, když *Al. exe* zkompiluje sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-153">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="21ce1-154">Do satelitního sestavení můžete vložit více souborů. Resources, ale pokud používáte model hvězdicového a hvězdicového modelu, je nutné pro každou jazykovou verzi zkompilovat jedno satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-154">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="21ce1-155">Můžete však vytvořit samostatné soubory. Resources pro řetězce a objekty.</span><span class="sxs-lookup"><span data-stu-id="21ce1-155">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="21ce1-156">Určuje jazykovou verzi prostředku, který má být zkompilován.</span><span class="sxs-lookup"><span data-stu-id="21ce1-156">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="21ce1-157">Modul CLR (Common Language Runtime) používá tyto informace při hledání prostředků pro zadanou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-157">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="21ce1-158">Pokud tuto možnost vynecháte, *Al. exe* přesto zkompiluje prostředek, ale modul runtime ho nebude moci najít, když si ho uživatel požádá.</span><span class="sxs-lookup"><span data-stu-id="21ce1-158">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="21ce1-159">Určuje název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="21ce1-159">Specifies the name of the output file.</span></span> <span data-ttu-id="21ce1-160">Název musí následovat po názvech standard *Base*. Resources. *přípona*, kde je *základem* název hlavního sestavení a *přípona* je platná přípona názvu souboru (například. dll).</span><span class="sxs-lookup"><span data-stu-id="21ce1-160">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="21ce1-161">Všimněte si, že modul runtime nemůže určit jazykovou verzi satelitního sestavení na základě názvu jeho výstupního souboru; k určení je nutné použít možnost **/culture** .</span><span class="sxs-lookup"><span data-stu-id="21ce1-161">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="21ce1-162">Určuje sestavení, ze kterého bude satelitní sestavení dědit všechna metadata sestavení kromě pole culture.</span><span class="sxs-lookup"><span data-stu-id="21ce1-162">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="21ce1-163">Tato možnost ovlivňuje satelitní sestavení pouze v případě, že zadáte sestavení se [silným názvem](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-163">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="21ce1-164">Úplný seznam možností dostupných pro *Al. exe*naleznete v tématu [Assembly Linker (Al. exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-164">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="21ce1-165">Satelitní sestavení: příklad</span><span class="sxs-lookup"><span data-stu-id="21ce1-165">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="21ce1-166">Následuje jednoduchý příklad "Hello World", který zobrazuje okno se zprávou obsahující lokalizovaný pozdrav.</span><span class="sxs-lookup"><span data-stu-id="21ce1-166">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="21ce1-167">Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie) a ruština (Rusko) a její záložní jazyková verze je angličtina.</span><span class="sxs-lookup"><span data-stu-id="21ce1-167">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="21ce1-168">Chcete-li vytvořit příklad, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="21ce1-168">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="21ce1-169">Vytvořte soubor prostředků s názvem *Greetings. resx* nebo *Greeting. txt* , který bude obsahovat prostředek pro výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-169">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="21ce1-170">Uloží jeden řetězec s názvem `HelloString` , jehož hodnota je Hello World!.</span><span class="sxs-lookup"><span data-stu-id="21ce1-170">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="21ce1-171">v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="21ce1-171">in this file.</span></span>

2. <span data-ttu-id="21ce1-172">Chcete-li označit, že angličtina (EN) je výchozí jazyková verze aplikace, přidejte <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> následující atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="21ce1-172">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. <span data-ttu-id="21ce1-173">Přidejte podporu pro další jazykové verze (EN-US, fr-FR a ru-RU) do aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="21ce1-173">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="21ce1-174">Pro podporu jazykové verze en-US nebo angličtiny (USA) vytvořte soubor prostředků s názvem *Greetings. en-US. resx* nebo *Greeting. en-US. txt*a uložte ho do něj s jediným řetězcem, `HelloString` jehož hodnota je "Hi World!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-174">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="21ce1-175">Pro podporu jazykové verze fr-FR nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *Greeting.fr-fr. resx* nebo *Greeting.fr-fr. txt*a uložte jej do něj jediným řetězcem s `HelloString` názvem, který má hodnotu "Salut tout Le Monde!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-175">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="21ce1-176">Pro podporu jazykové verze ru-RU nebo ruštiny (Rusko) vytvořte soubor prostředků s názvem *Greeting.ru-ru. resx* nebo *Greeting.ru-ru. txt*a uložte ho do něj s jedním řetězcem `HelloString` s názvem "Всем привет!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-176">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="21ce1-177">Pomocí [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) zkompilujte jednotlivé texty nebo soubory prostředků XML do binárního souboru *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-177">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="21ce1-178">Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-178">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="21ce1-179">Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="21ce1-179">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="21ce1-180">Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkazy pro zkompilování souborů *. resx* do souborů *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="21ce1-180">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="21ce1-181">Pokud jsou vaše prostředky v textových souborech namísto souborů XML, nahraďte příponu *. resx* textem *. txt*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-181">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="21ce1-182">Zkompilujte následující zdrojový kód spolu s prostředky pro výchozí jazykovou verzi do hlavního sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="21ce1-182">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="21ce1-183">Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání konstruktoru <xref:System.Resources.ResourceManager> třídy na následující:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="21ce1-183">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="21ce1-184">Pokud je aplikace pojmenována jako příklad a kompilujete z příkazového řádku, příkaz pro kompilátor jazyka C# je:</span><span class="sxs-lookup"><span data-stu-id="21ce1-184">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="21ce1-185">Odpovídající příkaz kompilátoru Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="21ce1-185">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="21ce1-186">Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="21ce1-186">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="21ce1-187">Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-187">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="21ce1-188">Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="21ce1-188">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="21ce1-189">Do satelitních sestavení vložte jednotlivé soubory *. Resources* specifické pro jazykovou verzi a uložte je do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="21ce1-189">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="21ce1-190">Příkaz k tomuto účelu pro každý soubor *. Resources* je:</span><span class="sxs-lookup"><span data-stu-id="21ce1-190">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="21ce1-191">kde *culture* je název jazykové verze, jejíž prostředky obsahuje satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-191">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="21ce1-192">Visual Studio zpracovává tento proces automaticky.</span><span class="sxs-lookup"><span data-stu-id="21ce1-192">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="21ce1-193">Pak můžete spustit příklad.</span><span class="sxs-lookup"><span data-stu-id="21ce1-193">You can then run the example.</span></span> <span data-ttu-id="21ce1-194">Bude náhodně vydávat jednu z podporovaných kultur aktuální jazykové verzi a zobrazí lokalizovaný pozdrav.</span><span class="sxs-lookup"><span data-stu-id="21ce1-194">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="21ce1-195">Instalace satelitních sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="21ce1-195">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="21ce1-196">Namísto instalace sestavení v podadresáři místní aplikace je můžete nainstalovat do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="21ce1-196">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="21ce1-197">To je zvlášť užitečné, pokud máte knihovny tříd a sestavení prostředků knihovny tříd, které jsou používány více aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-197">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="21ce1-198">Instalace sestavení do globální mezipaměti sestavení vyžaduje, aby měly silné názvy.</span><span class="sxs-lookup"><span data-stu-id="21ce1-198">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="21ce1-199">Sestavení se silným názvem jsou podepsaná s platnou dvojicí veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21ce1-199">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="21ce1-200">Obsahují informace o verzi, kterou modul runtime používá k určení sestavení, které se má použít pro splnění požadavku vazby.</span><span class="sxs-lookup"><span data-stu-id="21ce1-200">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="21ce1-201">Další informace o silných názvech a verzích najdete v tématu [Správa verzí sestavení](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-201">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="21ce1-202">Další informace o silných názvech naleznete v tématu [sestavení se silným názvem](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-202">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="21ce1-203">Při vývoji aplikace je nepravděpodobné, že budete mít přístup k finálnímu páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21ce1-203">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="21ce1-204">Chcete-li nainstalovat satelitní sestavení v globální mezipaměti sestavení (GAC) a zajistit, že funguje podle očekávání, můžete použít techniku nazvanou zpožděné podepisování.</span><span class="sxs-lookup"><span data-stu-id="21ce1-204">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="21ce1-205">Při zpoždění podepsání sestavení v okamžiku sestavení rezervujete místo v souboru pro podpis silného názvu.</span><span class="sxs-lookup"><span data-stu-id="21ce1-205">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="21ce1-206">Vlastní podepisování je zpožděné až později, až bude dostupný poslední pár veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21ce1-206">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="21ce1-207">Další informace o zpožděném podepisování naleznete v tématu [Delay Signing Assembly](../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-207">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="21ce1-208">Získání veřejného klíče</span><span class="sxs-lookup"><span data-stu-id="21ce1-208">Obtaining the Public Key</span></span>

<span data-ttu-id="21ce1-209">Chcete-li zpozdit podepsání sestavení, je nutné mít přístup k veřejnému klíči.</span><span class="sxs-lookup"><span data-stu-id="21ce1-209">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="21ce1-210">Můžete buď získat skutečný veřejný klíč z organizace ve vaší společnosti, který provede případné podepisování, nebo vytvořit veřejný klíč pomocí [nástroje Strong Name (Sn. exe)](../tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-210">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="21ce1-211">Následující příkaz *sn. exe* vytvoří dvojici veřejného a privátního klíče testu.</span><span class="sxs-lookup"><span data-stu-id="21ce1-211">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="21ce1-212">Možnost **– k** určuje, že *sn. exe* by měl vytvořit nový pár klíčů a uložit ho do souboru s názvem *TestKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-212">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="21ce1-213">Veřejný klíč můžete extrahovat ze souboru, který obsahuje pár testovacích klíčů.</span><span class="sxs-lookup"><span data-stu-id="21ce1-213">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="21ce1-214">Následující příkaz extrahuje veřejný klíč z *TestKeyPair. snk* a uloží jej do *PublicKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="21ce1-214">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="21ce1-215">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="21ce1-215">Delay Signing an Assembly</span></span>

<span data-ttu-id="21ce1-216">Po získání nebo vytvoření veřejného klíče použijete [linker sestavení (Al. exe)](../tools/al-exe-assembly-linker.md) ke kompilaci sestavení a zadáte zpožděné podepisování.</span><span class="sxs-lookup"><span data-stu-id="21ce1-216">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="21ce1-217">Následující příkaz *Al. exe* vytvoří satelitní sestavení se silným názvem pro aplikaci StringLibrary ze souboru *strings. ja. Resources* :</span><span class="sxs-lookup"><span data-stu-id="21ce1-217">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="21ce1-218">Možnost **-Delay +** určuje, že linker sestavení by měl zpozdit podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-218">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="21ce1-219">Možnost **-keyfile** Určuje název souboru klíče, který obsahuje veřejný klíč, který se použije pro Zpožděné podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-219">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="21ce1-220">Opětovné podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="21ce1-220">Re-signing an Assembly</span></span>

<span data-ttu-id="21ce1-221">Před nasazením aplikace je nutné znovu podepsat zpožděné satelitní sestavení se skutečným párem klíčů.</span><span class="sxs-lookup"><span data-stu-id="21ce1-221">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="21ce1-222">To lze provést pomocí programu *sn. exe*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-222">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="21ce1-223">Následující příkaz *sn. exe* podepíše *StringLibrary. Resources. dll* dvojici klíčů uloženou v souboru *RealKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-223">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="21ce1-224">Možnost **– R** určuje, že dříve podepsané nebo zpožděné podepsané sestavení má být znovu podepsáno.</span><span class="sxs-lookup"><span data-stu-id="21ce1-224">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="21ce1-225">Instalace satelitního sestavení do globální mezipaměti sestavení (GAC)</span><span class="sxs-lookup"><span data-stu-id="21ce1-225">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="21ce1-226">Pokud modul runtime vyhledává prostředky v záložním procesu prostředků, hledá nejprve [globální mezipaměť sestavení (GAC](../app-domains/gac.md) ).</span><span class="sxs-lookup"><span data-stu-id="21ce1-226">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="21ce1-227">(Další informace najdete v části "proces záložního prostředku" v tématu [balení a nasazení prostředků](packaging-and-deploying-resources-in-desktop-apps.md) .) Jakmile je satelitní sestavení podepsáno silným názvem, lze jej nainstalovat do globální mezipaměti sestavení [(GAC) pomocí nástroj Global Assembly Cache Tool (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-227">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="21ce1-228">Následující příkaz *Gacutil. exe* nainstaluje *StringLibrary. Resources. dll*\* do globální mezipaměti sestavení (GAC):</span><span class="sxs-lookup"><span data-stu-id="21ce1-228">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="21ce1-229">Možnost **/i** určuje, že nástroj *Gacutil. exe* by měl nainstalovat zadané sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="21ce1-229">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="21ce1-230">Po instalaci satelitního sestavení v mezipaměti budou prostředky, které obsahuje, zpřístupněny všem aplikacím, které jsou navrženy pro použití satelitního sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-230">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="21ce1-231">Prostředky v globální mezipaměti sestavení (GAC): příklad</span><span class="sxs-lookup"><span data-stu-id="21ce1-231">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="21ce1-232">Následující příklad používá metodu v knihovně tříd .NET Framework k extrakci a vrácení lokalizovaného pozdravu ze souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="21ce1-232">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="21ce1-233">Knihovna a její prostředky jsou registrovány v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="21ce1-233">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="21ce1-234">Příklad obsahuje prostředky pro angličtinu (USA), francouzština (Francie), ruština (Rusko) a anglické kultury.</span><span class="sxs-lookup"><span data-stu-id="21ce1-234">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="21ce1-235">Výchozí jazyková verze je angličtina; jeho prostředky jsou uloženy v hlavním sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-235">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="21ce1-236">Příklad prvotního zpoždění podepíše knihovnu a její satelitní sestavení pomocí veřejného klíče a pak je znovu podepíše s párem veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21ce1-236">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="21ce1-237">Chcete-li vytvořit příklad, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="21ce1-237">To create the example, do the following:</span></span>

1. <span data-ttu-id="21ce1-238">Pokud nepoužíváte aplikaci Visual Studio, použijte následující příkaz se [silným názvem (Sn. exe)](../tools/sn-exe-strong-name-tool.md) a vytvořte dvojici veřejného a privátního klíče s názvem *ResKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="21ce1-238">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="21ce1-239">Pokud používáte sadu Visual Studio, použijte k vygenerování souboru klíče kartu **podepisování** v dialogovém okně **vlastnosti** projektu.</span><span class="sxs-lookup"><span data-stu-id="21ce1-239">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="21ce1-240">Použijte následující příkaz se [silným názvem (Sn. exe)](../tools/sn-exe-strong-name-tool.md) a vytvořte soubor veřejného klíče s názvem *PublicKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="21ce1-240">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="21ce1-241">Vytvořte soubor prostředků s názvem *strings. resx* , který bude obsahovat prostředek pro výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="21ce1-241">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="21ce1-242">Uložte jeden řetězec s názvem `Greeting` , jehož hodnota je "jak provést?"</span><span class="sxs-lookup"><span data-stu-id="21ce1-242">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="21ce1-243">v tomto souboru.</span><span class="sxs-lookup"><span data-stu-id="21ce1-243">in that file.</span></span>

4. <span data-ttu-id="21ce1-244">Chcete-li označit, že "en" je výchozí jazykovou verzí aplikace, <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> přidejte následující atribut do souboru AssemblyInfo aplikace nebo do hlavního souboru zdrojového kódu, který bude zkompilován do hlavního sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="21ce1-244">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="21ce1-245">Přidejte podporu pro další jazykové verze (kultury en-US, fr-FR a ru-RU) do aplikace následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="21ce1-245">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="21ce1-246">Chcete-li podporovat jazykovou verzi "en-US" nebo anglickou (USA), vytvořte soubor prostředků s názvem *strings. en-US. resx* nebo *String. en-US. txt*a uložte jej do něj jediným `Greeting` řetězcem s názvem "Hello!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-246">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="21ce1-247">Pro podporu "fr-FR" nebo francouzštiny (Francie) vytvořte soubor prostředků s názvem *strings.fr-fr. resx* nebo *strings.fr-fr. txt* a uložte jej do něj jediným řetězcem, `Greeting` jehož hodnota je "šťastnou jour!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-247">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="21ce1-248">Pro podporu "ru-RU" nebo ruské jazykové verze (Rusko) vytvořte soubor prostředků s názvem *strings.ru-ru. resx* nebo *strings.ru-ru. txt* a uložte do něj jediný řetězec s názvem `Greeting` , jehož hodnota je "привет!".</span><span class="sxs-lookup"><span data-stu-id="21ce1-248">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="21ce1-249">Pomocí [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) zkompilujte jednotlivé texty nebo soubory prostředků XML do binárního souboru. Resources.</span><span class="sxs-lookup"><span data-stu-id="21ce1-249">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="21ce1-250">Výstupem je sada souborů, které mají stejný název kořenového souboru jako soubory *. resx* nebo *. txt* , ale rozšíření *. Resources* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-250">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="21ce1-251">Pokud vytvoříte příklad se sadou Visual Studio, proces kompilace se zpracuje automaticky.</span><span class="sxs-lookup"><span data-stu-id="21ce1-251">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="21ce1-252">Pokud nepoužíváte aplikaci Visual Studio, spusťte následující příkaz pro zkompilování souborů *. resx* do souborů *. Resources* :</span><span class="sxs-lookup"><span data-stu-id="21ce1-252">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="21ce1-253">Kde *filename* je volitelná cesta, název souboru a Přípona souboru *. resx* nebo textového souboru.</span><span class="sxs-lookup"><span data-stu-id="21ce1-253">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="21ce1-254">Zkompilujte následující zdrojový kód pro *StringLibrary. vb* nebo *StringLibrary.cs* společně s prostředky pro výchozí jazykovou verzi do zpožděně podepsaného sestavení knihovny s názvem *StringLibrary. dll*:</span><span class="sxs-lookup"><span data-stu-id="21ce1-254">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="21ce1-255">Pokud používáte příkazový řádek místo sady Visual Studio k vytvoření příkladu, měli byste změnit volání konstruktoru <xref:System.Resources.ResourceManager> třídy na. `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="21ce1-255">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="21ce1-256">Příkaz pro kompilátor jazyka C# je:</span><span class="sxs-lookup"><span data-stu-id="21ce1-256">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="21ce1-257">Odpovídající příkaz kompilátoru Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="21ce1-257">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="21ce1-258">Vytvořte podadresář v hlavním adresáři aplikace pro každou lokalizovanou jazykovou verzi, kterou aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="21ce1-258">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="21ce1-259">Měli byste vytvořit podadresář *en-US*, *fr-FR*a *ru-ru* .</span><span class="sxs-lookup"><span data-stu-id="21ce1-259">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="21ce1-260">Visual Studio vytvoří tyto podadresáře automaticky v rámci procesu kompilace.</span><span class="sxs-lookup"><span data-stu-id="21ce1-260">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="21ce1-261">Vzhledem k tomu, že všechna satelitní sestavení mají stejný název souboru, podadresáře se používají k ukládání jednotlivých satelitních sestavení specifických pro jazykovou verzi, dokud nejsou podepsány pomocí páru veřejného a privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="21ce1-261">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="21ce1-262">Vložte jednotlivé soubory *prostředků* specifické pro jazykovou verzi do zpožděně podepsaných satelitních sestavení a uložte je do příslušného adresáře.</span><span class="sxs-lookup"><span data-stu-id="21ce1-262">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="21ce1-263">Příkaz k tomuto účelu pro každý soubor *. Resources* je:</span><span class="sxs-lookup"><span data-stu-id="21ce1-263">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="21ce1-264">kde *culture* je název jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="21ce1-264">where *culture* is the name of a culture.</span></span> <span data-ttu-id="21ce1-265">V tomto příkladu jsou názvy jazykové verze en-US, fr-FR a ru-RU.</span><span class="sxs-lookup"><span data-stu-id="21ce1-265">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="21ce1-266">Znovu podepište *StringLibrary. dll* pomocí [nástroje Strong Name (Sn. exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="21ce1-266">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="21ce1-267">Znovu podepište jednotlivá satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="21ce1-267">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="21ce1-268">Chcete-li to provést, použijte [Nástroj Strong Name (Sn. exe)](../tools/sn-exe-strong-name-tool.md) následujícím způsobem pro každé satelitní sestavení:</span><span class="sxs-lookup"><span data-stu-id="21ce1-268">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="21ce1-269">Zaregistrujte *StringLibrary. dll* a každé z jeho satelitních sestavení v globální mezipaměti sestavení (GAC) pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="21ce1-269">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="21ce1-270">kde *filename* je název souboru, který se má zaregistrovat.</span><span class="sxs-lookup"><span data-stu-id="21ce1-270">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="21ce1-271">Pokud používáte aplikaci Visual Studio, vytvořte nový projekt **konzolové aplikace** s názvem `Example`, do něj přidejte odkaz na *StringLibrary. dll* a následující zdrojový kód a zkompilujte.</span><span class="sxs-lookup"><span data-stu-id="21ce1-271">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="21ce1-272">Pro zkompilování z příkazového řádku, použijte následující příkaz pro kompilátor jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="21ce1-272">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="21ce1-273">Příkazový řádek pro kompilátor Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="21ce1-273">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="21ce1-274">Spusťte *příklad. exe*.</span><span class="sxs-lookup"><span data-stu-id="21ce1-274">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="21ce1-275">Viz také</span><span class="sxs-lookup"><span data-stu-id="21ce1-275">See also</span></span>

- [<span data-ttu-id="21ce1-276">Zabalení a nasazení prostředků</span><span class="sxs-lookup"><span data-stu-id="21ce1-276">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="21ce1-277">Zpoždění podepsání sestavení</span><span class="sxs-lookup"><span data-stu-id="21ce1-277">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="21ce1-278">Al. exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="21ce1-278">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="21ce1-279">SN. exe (Nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="21ce1-279">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="21ce1-280">Gacutil. exe (nástroj Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="21ce1-280">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="21ce1-281">Prostředky v aplikacích klasické pracovní plochy</span><span class="sxs-lookup"><span data-stu-id="21ce1-281">Resources in Desktop Apps</span></span>](index.md)
