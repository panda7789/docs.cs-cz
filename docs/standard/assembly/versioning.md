---
title: Správa verzí sestavení
description: Přečtěte si o verzích sestavení .NET. Všechny verze sestavení, které používají CLR, jsou provedeny na úrovni sestavení.
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: fdffbcc0bbafed62228cba35e8f85fbec7f7fbab
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380073"
---
# <a name="assembly-versioning"></a><span data-ttu-id="1db54-104">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="1db54-104">Assembly versioning</span></span>

<span data-ttu-id="1db54-105">Všechna verze sestavení, která používají modul CLR (Common Language Runtime), je provedena na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-105">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="1db54-106">Konkrétní verze sestavení a verze závislých sestavení jsou zaznamenány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-106">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="1db54-107">Výchozí zásadou verze modulu runtime je, že aplikace běží pouze s verzemi, které byly vytvořeny a testovány pomocí nástroje, pokud nejsou přepsány explicitními zásadami verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a konfigurační soubor správce počítače).</span><span class="sxs-lookup"><span data-stu-id="1db54-107">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1db54-108">Správa verzí se provádí pouze v sestaveních se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="1db54-108">Versioning is done only on assemblies with strong names.</span></span>  
  
<span data-ttu-id="1db54-109">Modul runtime provede několik kroků pro vyřešení požadavku vazby sestavení:</span><span class="sxs-lookup"><span data-stu-id="1db54-109">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1. <span data-ttu-id="1db54-110">Zkontroluje původní odkaz na sestavení a určí verzi sestavení, která se má svázat.</span><span class="sxs-lookup"><span data-stu-id="1db54-110">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2. <span data-ttu-id="1db54-111">Kontroluje všechny použitelné konfigurační soubory pro použití zásad verze.</span><span class="sxs-lookup"><span data-stu-id="1db54-111">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3. <span data-ttu-id="1db54-112">Určuje správné sestavení z původního odkazu na sestavení a veškeré přesměrování zadané v konfiguračních souborech a určuje verzi, která má být svázána s volajícím sestavením.</span><span class="sxs-lookup"><span data-stu-id="1db54-112">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4. <span data-ttu-id="1db54-113">Kontroluje globální mezipaměť sestavení (GAC), základy kódu zadané v konfiguračních souborech a pak kontroluje adresář a podadresáře aplikace pomocí pravidel pro zjišťování, která jsou vysvětlena v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1db54-113">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
<span data-ttu-id="1db54-114">Následující ilustrace znázorňuje tyto kroky:</span><span class="sxs-lookup"><span data-stu-id="1db54-114">The following illustration shows these steps:</span></span>  
  
![Diagram, který ukazuje kroky v řešení požadavků vazby sestavení](./media/versioning/resolve-assembly-binding-request.gif)
  
<span data-ttu-id="1db54-116">Další informace o konfiguraci aplikací najdete v tématu [Konfigurace](../../framework/configure-apps/index.md)aplikací.</span><span class="sxs-lookup"><span data-stu-id="1db54-116">For more information about configuring applications, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="1db54-117">Další informace o zásadách vázání najdete v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1db54-117">For more information about binding policy, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="1db54-118">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="1db54-118">Version information</span></span>  

<span data-ttu-id="1db54-119">Každé sestavení má dva různé způsoby, jak vyjádřit informace o verzi:</span><span class="sxs-lookup"><span data-stu-id="1db54-119">Each assembly has two distinct ways of expressing version information:</span></span>  
  
- <span data-ttu-id="1db54-120">Číslo verze sestavení, které spolu s názvem sestavení a informacemi o jazykové verzi, je součástí identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-120">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="1db54-121">Toto číslo používá modul runtime k vyhodnocování zásad verze a hraje v procesu rozlišení typu za běhu klíčovou část.</span><span class="sxs-lookup"><span data-stu-id="1db54-121">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
- <span data-ttu-id="1db54-122">Informační verze, což je řetězec, který představuje další informace o verzi obsažené pouze pro informativní účely.</span><span class="sxs-lookup"><span data-stu-id="1db54-122">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="1db54-123">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="1db54-123">Assembly version number</span></span>  

<span data-ttu-id="1db54-124">Každé sestavení má v rámci své identity číslo verze.</span><span class="sxs-lookup"><span data-stu-id="1db54-124">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="1db54-125">V takovém případě se dvě sestavení, která se liší číslem verze, považují za modul runtime za zcela odlišná sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-125">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="1db54-126">Toto číslo verze je fyzicky reprezentované jako řetězec o čtyřech částech v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="1db54-126">This version number is physically represented as a four-part string with the following format:</span></span>  
  
<span data-ttu-id="1db54-127">\<> *hlavní verze* . \< *vedlejší verze*>. \< *číslo buildu*>. \< *Revize*></span><span class="sxs-lookup"><span data-stu-id="1db54-127">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
<span data-ttu-id="1db54-128">Například verze 1.5.1254.0 označuje 1 jako hlavní verzi, 5 jako dílčí verzi, 1254 jako číslo sestavení a 0 jako číslo revize.</span><span class="sxs-lookup"><span data-stu-id="1db54-128">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
<span data-ttu-id="1db54-129">Číslo verze je uloženo v manifestu sestavení spolu s dalšími informacemi o identitě, včetně názvu sestavení a veřejného klíče, a také informace o relacích a identitách jiných sestavení připojených k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1db54-129">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
<span data-ttu-id="1db54-130">Při sestavování sestavení Nástroj pro vývoj zaznamenává informace o závislostech pro každé sestavení, na které je odkazováno v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-130">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="1db54-131">Modul runtime používá tato čísla verzí ve spojení s konfiguračními informacemi nastavenými správcem, aplikací nebo vydavatelem k načtení správné verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="1db54-131">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
<span data-ttu-id="1db54-132">Modul runtime rozlišuje běžné a silně pojmenované sestavení pro účely správy verzí.</span><span class="sxs-lookup"><span data-stu-id="1db54-132">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="1db54-133">Kontrola verze se vyskytuje pouze u sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="1db54-133">Version checking only occurs with strong-named assemblies.</span></span>  
  
<span data-ttu-id="1db54-134">Informace o zadávání zásad vázání verzí najdete v tématu [Konfigurace aplikací](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="1db54-134">For information about specifying version binding policies, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="1db54-135">Informace o tom, jak modul runtime používá informace o verzi k nalezení konkrétního sestavení, naleznete v tématu [jak modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1db54-135">For information about how the runtime uses version information to find a particular assembly, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="1db54-136">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="1db54-136">Assembly informational version</span></span>  

<span data-ttu-id="1db54-137">Informační verze je řetězec, který připojuje informace o dalších verzích k sestavení pouze pro informativní účely. Tyto informace se nepoužívají v době běhu.</span><span class="sxs-lookup"><span data-stu-id="1db54-137">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="1db54-138">Textová informační verze odpovídá marketingové dokumentaci produktu, balení nebo názvu produktu a není používána modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="1db54-138">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="1db54-139">Informační verze může být například "modul common language runtime verze 1,0" nebo "NET Control SP 2".</span><span class="sxs-lookup"><span data-stu-id="1db54-139">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="1db54-140">Na kartě verze v dialogovém okně Vlastnosti souboru v systému Microsoft Windows se tyto informace zobrazí v položce "verze produktu".</span><span class="sxs-lookup"><span data-stu-id="1db54-140">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1db54-141">I když můžete zadat libovolný text, zobrazí se při kompilaci zpráva upozornění, pokud řetězec není ve formátu používaném číslem verze sestavení, nebo pokud je v tomto formátu, ale obsahuje zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="1db54-141">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="1db54-142">Toto upozornění je neškodné.</span><span class="sxs-lookup"><span data-stu-id="1db54-142">This warning is harmless.</span></span>  
  
<span data-ttu-id="1db54-143">Informační verze je reprezentovaná pomocí vlastního atributu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="1db54-143">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1db54-144">Další informace o atributu informační verze naleznete v tématu [set Assembly Attributes](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1db54-144">For more information about the informational version attribute, see [Set assembly attributes](set-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db54-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db54-145">See also</span></span>

- [<span data-ttu-id="1db54-146">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="1db54-146">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1db54-147">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="1db54-147">Configure apps</span></span>](../../framework/configure-apps/index.md)
- [<span data-ttu-id="1db54-148">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="1db54-148">Set assembly attributes</span></span>](set-attributes.md)
- [<span data-ttu-id="1db54-149">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="1db54-149">Assemblies in .NET</span></span>](index.md)
