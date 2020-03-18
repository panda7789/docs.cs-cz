---
title: Správa verzí sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: bbb3dae2ce66c93d05a2a1c0f7e426901fa7b2e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140175"
---
# <a name="assembly-versioning"></a><span data-ttu-id="6bbf5-102">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="6bbf5-102">Assembly versioning</span></span>

<span data-ttu-id="6bbf5-103">Všechna správa verzí sestavení, které používají za běhu společného jazyka, se provádějí na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="6bbf5-104">Konkrétní verze sestavení a verze závislých sestavení jsou zaznamenány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="6bbf5-105">Výchozí zásadou verze pro běhový čas je, že aplikace běží pouze s verzemi, které byly vytvořeny a testovány, pokud nejsou přepsány explicitními zásadami verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a konfiguračního souboru správce počítače).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bbf5-106">Správa verzí se provádí pouze na sestaveních se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-106">Versioning is done only on assemblies with strong names.</span></span>  
  
<span data-ttu-id="6bbf5-107">Runtime provede několik kroků k vyřešení požadavku na vazbu sestavení:</span><span class="sxs-lookup"><span data-stu-id="6bbf5-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1. <span data-ttu-id="6bbf5-108">Zkontroluje původní odkaz na sestavení a určí verzi sestavení, která má být vázána.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2. <span data-ttu-id="6bbf5-109">Zkontroluje všechny příslušné konfigurační soubory, aby se použily zásady verze.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3. <span data-ttu-id="6bbf5-110">Určuje správné sestavení z původního odkazu sestavení a jakékoli přesměrování zadané v konfiguračních souborech a určuje verzi, která by měla být vázána na volající sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4. <span data-ttu-id="6bbf5-111">Zkontroluje globální mezipaměť sestavení, základy kódu zadané v konfiguračních souborech a potom zkontroluje adresář a podadresáře aplikace pomocí pravidel zjišťování vysvětlených v části [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
<span data-ttu-id="6bbf5-112">Následující obrázek znázorňuje tyto kroky:</span><span class="sxs-lookup"><span data-stu-id="6bbf5-112">The following illustration shows these steps:</span></span>  
  
![Diagram, který ukazuje kroky v řešení požadavku na vazbu sestavení.](./media/versioning/resolve-assembly-binding-request.gif)
  
<span data-ttu-id="6bbf5-114">Další informace o konfiguraci aplikací naleznete v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-114">For more information about configuring applications, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="6bbf5-115">Další informace o zásadách vazby naleznete [v tématu Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-115">For more information about binding policy, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="6bbf5-116">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="6bbf5-116">Version information</span></span>  

<span data-ttu-id="6bbf5-117">Každé sestavení má dva odlišné způsoby vyjádření informací o verzi:</span><span class="sxs-lookup"><span data-stu-id="6bbf5-117">Each assembly has two distinct ways of expressing version information:</span></span>  
  
- <span data-ttu-id="6bbf5-118">Číslo verze sestavení, které je spolu s názvem sestavení a informacemi o jazykové verzi součástí identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-118">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="6bbf5-119">Toto číslo používá za běhu k vynucení zásad verze a hraje klíčovou roli v procesu rozlišení typu za běhu.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-119">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
- <span data-ttu-id="6bbf5-120">Informační verze, což je řetězec, který představuje další informace o verzi zahrnuty pouze pro informační účely.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-120">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="6bbf5-121">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="6bbf5-121">Assembly version number</span></span>  

<span data-ttu-id="6bbf5-122">Každé sestavení má číslo verze jako součást své identity.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-122">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="6bbf5-123">Jako takové dvě sestavení, které se liší podle čísla verze jsou považovány za za zcela odlišné sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-123">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="6bbf5-124">Toto číslo verze je fyzicky reprezentováno jako čtyřdílný řetězec v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="6bbf5-124">This version number is physically represented as a four-part string with the following format:</span></span>  
  
<span data-ttu-id="6bbf5-125">\<*hlavní verze*>. \< *dílčí verze*>. \< *číslo sestavení*>. \< *revize*></span><span class="sxs-lookup"><span data-stu-id="6bbf5-125">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
<span data-ttu-id="6bbf5-126">Například verze 1.5.1254.0 označuje 1 jako hlavní verzi, 5 jako dílčí verzi, 1254 jako číslo sestavení a 0 jako číslo revize.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-126">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
<span data-ttu-id="6bbf5-127">Číslo verze je uloženo v manifestu sestavení spolu s dalšími informacemi o identitě, včetně názvu sestavení a veřejného klíče, stejně jako informace o vztazích a identitách jiných sestavení spojených s aplikací.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-127">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
<span data-ttu-id="6bbf5-128">Při sestavení sestavení nástroj pro vývoj zaznamenává informace o závislostech pro každé sestavení, na které se odkazuje v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-128">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="6bbf5-129">Runtime používá tato čísla verzí ve spojení s informacemi o konfiguraci nastavenými správcem, aplikací nebo vydavatelem k načtení správné verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-129">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
<span data-ttu-id="6bbf5-130">Runtime rozlišuje mezi pravidelnými a silnými pojmenovanými sestaveními pro účely správy verzí.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-130">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="6bbf5-131">Kontrola verze probíhá pouze u sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-131">Version checking only occurs with strong-named assemblies.</span></span>  
  
<span data-ttu-id="6bbf5-132">Informace o určení zásad vazby verzí naleznete v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-132">For information about specifying version binding policies, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="6bbf5-133">Informace o tom, jak runtime používá informace o verzi k vyhledání konkrétního sestavení, naleznete [v tématu Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-133">For information about how the runtime uses version information to find a particular assembly, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="6bbf5-134">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="6bbf5-134">Assembly informational version</span></span>  

<span data-ttu-id="6bbf5-135">Informační verze je řetězec, který připojuje další informace o verzi sestavení pouze pro informační účely; Tyto informace nejsou používány za běhu.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-135">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="6bbf5-136">Textová informační verze odpovídá marketingové literatuře, obalu nebo názvu produktu produktu a není používána za běhu.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-136">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="6bbf5-137">Informační verze může být například "Common Language Runtime verze 1.0" nebo "NET Control SP 2".</span><span class="sxs-lookup"><span data-stu-id="6bbf5-137">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="6bbf5-138">Na kartě Verze dialogového okna Vlastnosti souboru v systému Microsoft Windows se tyto informace zobrazí v položce Verze produktu.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-138">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bbf5-139">Přestože můžete zadat libovolný text, zobrazí se v kompilaci varovná zpráva, pokud řetězec není ve formátu používaném číslem verze sestavení nebo pokud je v tomto formátu, ale obsahuje zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-139">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="6bbf5-140">Toto upozornění je neškodné.</span><span class="sxs-lookup"><span data-stu-id="6bbf5-140">This warning is harmless.</span></span>  
  
<span data-ttu-id="6bbf5-141">Informační verze je reprezentována <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>pomocí vlastního atributu .</span><span class="sxs-lookup"><span data-stu-id="6bbf5-141">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6bbf5-142">Další informace o atributu informační verze naleznete v tématu [Set assembly attributes](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6bbf5-142">For more information about the informational version attribute, see [Set assembly attributes](set-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bbf5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bbf5-143">See also</span></span>

- [<span data-ttu-id="6bbf5-144">Jak runtime vyhledá sestavení</span><span class="sxs-lookup"><span data-stu-id="6bbf5-144">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6bbf5-145">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="6bbf5-145">Configure apps</span></span>](../../framework/configure-apps/index.md)
- [<span data-ttu-id="6bbf5-146">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="6bbf5-146">Set assembly attributes</span></span>](set-attributes.md)
- [<span data-ttu-id="6bbf5-147">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="6bbf5-147">Assemblies in .NET</span></span>](index.md)
