---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6a10a896494304b9c3c17bc320464a8273e430d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752127"
---
# <a name="assembly-placement"></a><span data-ttu-id="93f20-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="93f20-102">Assembly Placement</span></span>
<span data-ttu-id="93f20-103">Pro většinu aplikací rozhraní .NET Framework vyhledejte sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení).</span><span class="sxs-lookup"><span data-stu-id="93f20-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="93f20-104">Můžete přepsat, kde modul common language runtime vyhledává sestavení pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="93f20-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="93f20-105">Pokud sestavení nemá silný název, umístění, pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresář aplikace nebo podadresáři.</span><span class="sxs-lookup"><span data-stu-id="93f20-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="93f20-106">Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) můžete zadat jakékoli umístění v počítači nebo v síti.</span><span class="sxs-lookup"><span data-stu-id="93f20-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="93f20-107">Podobně jako pravidla použít k vyhledání sestavení při práci s nespravovaným kódem nebo aplikace zprostředkovatele komunikace s objekty COM: Pokud sestavení budou sdílet více aplikací, by měly být nainstalovány do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="93f20-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="93f20-108">Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovny typů a zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="93f20-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="93f20-109">Sestavení používá zprostředkovatel komunikace s objekty COM musí být zaregistrován v katalogu, i když v některých případech se tato registrace probíhá automaticky.</span><span class="sxs-lookup"><span data-stu-id="93f20-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f20-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="93f20-110">See Also</span></span>  
 [<span data-ttu-id="93f20-111">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="93f20-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="93f20-112">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="93f20-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="93f20-113">Interoperabilita modelů COM Upřesnit</span><span class="sxs-lookup"><span data-stu-id="93f20-113">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/library/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="93f20-114">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="93f20-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
