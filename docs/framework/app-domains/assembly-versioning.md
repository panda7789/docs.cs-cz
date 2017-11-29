---
title: "Správa verzí sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a956e0c4521e4a1079b331868e811e68af2e710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-versioning"></a><span data-ttu-id="0fee2-102">Správa verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="0fee2-102">Assembly Versioning</span></span>
<span data-ttu-id="0fee2-103">Všechny verze sestavení, které používají modul common language runtime se provádí na úrovni sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="0fee2-104">Konkrétní verze sestavení a verze závislé sestavení jsou popsané v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="0fee2-105">Výchozí zásada verze pro modul runtime je, že aplikace spouštět pouze s verzemi, které by byly vytvořené a testovány, není-li přepsat zásady explicitní verze v konfiguračních souborech (konfigurační soubor aplikace, soubor zásad vydavatele a Správce konfigurace souboru počítače).</span><span class="sxs-lookup"><span data-stu-id="0fee2-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fee2-106">Správa verzí se provádí pouze na sestavení se silnými názvy.</span><span class="sxs-lookup"><span data-stu-id="0fee2-106">Versioning is done only on assemblies with strong names.</span></span>  
  
 <span data-ttu-id="0fee2-107">Modul runtime provede několik postup řešení požadavků sestavení na vazby:</span><span class="sxs-lookup"><span data-stu-id="0fee2-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1.  <span data-ttu-id="0fee2-108">Kontroluje původní odkaz sestavení zjistíte verzi sestavení, které má být vázána.</span><span class="sxs-lookup"><span data-stu-id="0fee2-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2.  <span data-ttu-id="0fee2-109">Kontroluje všechny vhodné konfigurační soubory pro použití zásad správy verzí.</span><span class="sxs-lookup"><span data-stu-id="0fee2-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3.  <span data-ttu-id="0fee2-110">Určuje správné sestavení z původní odkaz sestavení a žádné přesměrování zadaný v konfiguračních souborech a určuje verzi, která by měla být vázána na volajícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4.  <span data-ttu-id="0fee2-111">Kontroluje globální mezipaměti sestavení, základy kódu v konfigurační soubory a pak kontroluje adresář aplikace a podadresáře pomocí pravidel zjišťování podrobně [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="0fee2-112">Následující obrázek znázorňuje tyto kroky.</span><span class="sxs-lookup"><span data-stu-id="0fee2-112">The following illustration shows these steps.</span></span>  
  
 <span data-ttu-id="0fee2-113">![.Assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span><span class="sxs-lookup"><span data-stu-id="0fee2-113">![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span></span>  
<span data-ttu-id="0fee2-114">Řešení požadavků sestavení na vazby</span><span class="sxs-lookup"><span data-stu-id="0fee2-114">Resolving an assembly binding request</span></span>  
  
 <span data-ttu-id="0fee2-115">Další informace o konfiguraci aplikací najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-115">For more information about configuring applications, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="0fee2-116">Další informace o zásadách vazby najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-116">For more information about binding policy, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="0fee2-117">Informace o verzi</span><span class="sxs-lookup"><span data-stu-id="0fee2-117">Version Information</span></span>  
 <span data-ttu-id="0fee2-118">Každé sestavení má dva odlišné způsoby vyjádření informace o verzi:</span><span class="sxs-lookup"><span data-stu-id="0fee2-118">Each assembly has two distinct ways of expressing version information:</span></span>  
  
-   <span data-ttu-id="0fee2-119">Číslo verze sestavení, které společně s informace o sestavení název a jazykovou verzi je součástí identity sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-119">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="0fee2-120">Toto číslo se používá modulem runtime k vynucení zásad správy verzí a hraje část klíče v procesu překladu, který typ za běhu.</span><span class="sxs-lookup"><span data-stu-id="0fee2-120">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
-   <span data-ttu-id="0fee2-121">Informační verzi, která je řetězec, který představuje další informace o verzi zahrnuty pouze pro informační účely.</span><span class="sxs-lookup"><span data-stu-id="0fee2-121">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="0fee2-122">Číslo verze sestavení</span><span class="sxs-lookup"><span data-stu-id="0fee2-122">Assembly Version Number</span></span>  
 <span data-ttu-id="0fee2-123">Každé sestavení má číslo verze jako součást svou identitu.</span><span class="sxs-lookup"><span data-stu-id="0fee2-123">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="0fee2-124">Jako takový dvou sestavení, které se liší podle čísla verze jsou považovány za modulem runtime úplně jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-124">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="0fee2-125">Toto číslo verze je fyzicky reprezentována jako řetězec sestávající ze čtyř částí v následujícím formátu:</span><span class="sxs-lookup"><span data-stu-id="0fee2-125">This version number is physically represented as a four-part string with the following format:</span></span>  
  
 <span data-ttu-id="0fee2-126">\<*hlavní verze*>.\< *podverze*>.\< *číslo sestavení*>.\< *revize*></span><span class="sxs-lookup"><span data-stu-id="0fee2-126">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
 <span data-ttu-id="0fee2-127">Například verze 1.5.1254.0 označuje 1 jako hlavní verze 5 jako podverzi, 1254 jako číslo sestavení a 0 jako číslo revize.</span><span class="sxs-lookup"><span data-stu-id="0fee2-127">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
 <span data-ttu-id="0fee2-128">Číslo verze je uložené v manifestu sestavení společně s dalšími informacemi o identitě včetně na název sestavení a veřejný klíč, a také informace o relacích a identitách jiných sestavení spojených s aplikací.</span><span class="sxs-lookup"><span data-stu-id="0fee2-128">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
 <span data-ttu-id="0fee2-129">Pokud sestavení vytvořené, vývoj nástroj zaznamenává informace o závislostech pro každé sestavení, který se odkazuje v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-129">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="0fee2-130">Modul runtime používá tato čísla verze ve spojení s informace o konfiguraci, která nastavuje správce, aplikace nebo vydavatel, k načtení správné verze odkazovaného sestavení.</span><span class="sxs-lookup"><span data-stu-id="0fee2-130">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
 <span data-ttu-id="0fee2-131">Modul runtime rozlišuje mezi obyčejnými a silným názvem sestavení pro účely správy verzí.</span><span class="sxs-lookup"><span data-stu-id="0fee2-131">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="0fee2-132">Kontrola verze dochází pouze s sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0fee2-132">Version checking only occurs with strong-named assemblies.</span></span>  
  
 <span data-ttu-id="0fee2-133">Informace o zadávání verze vazby zásady najdete v tématu [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-133">For information about specifying version binding policies, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="0fee2-134">Informace o tom, jak modul runtime používá informace o verzi k vyhledání konkrétního sestavení najdete v tématu [jak modul Runtime vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-134">For information about how the runtime uses version information to find a particular assembly, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="0fee2-135">Informační verze sestavení</span><span class="sxs-lookup"><span data-stu-id="0fee2-135">Assembly Informational Version</span></span>  
 <span data-ttu-id="0fee2-136">Informační verze je řetězec, který se připojuje k sestavení Další informace o verzi pro informační účely pouze; Tyto informace se nepoužívá v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0fee2-136">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="0fee2-137">Informační verze založený na textu odpovídá produktu marketingové dokumentace, balení nebo název produktu a nepoužívá modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="0fee2-137">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="0fee2-138">Informační verze může být například "Common Language Runtime verze 1.0" nebo "NET řízení SP 2".</span><span class="sxs-lookup"><span data-stu-id="0fee2-138">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="0fee2-139">Na kartě verze v dialogovém okně vlastností souboru v systému Windows tato informace se zobrazí v položce "Verzí produktu".</span><span class="sxs-lookup"><span data-stu-id="0fee2-139">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fee2-140">I když můžete zadat libovolný text, upozornění se zobrazí při kompilaci, pokud řetězec není ve formátu používá číslo verze sestavení, nebo pokud je v tomto formátu, ale obsahuje zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="0fee2-140">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="0fee2-141">Toto upozornění je neškodné.</span><span class="sxs-lookup"><span data-stu-id="0fee2-141">This warning is harmless.</span></span>  
  
 <span data-ttu-id="0fee2-142">Informační verze je reprezentována pomocí vlastního atributu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0fee2-142">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0fee2-143">Další informace o atributu informační verze najdete v tématu [nastavení atributů sestavení](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0fee2-143">For more information about the informational version attribute, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fee2-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fee2-144">See Also</span></span>  
 [<span data-ttu-id="0fee2-145">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="0fee2-145">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="0fee2-146">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="0fee2-146">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="0fee2-147">Nastavování atributů sestavení</span><span class="sxs-lookup"><span data-stu-id="0fee2-147">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [<span data-ttu-id="0fee2-148">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="0fee2-148">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
