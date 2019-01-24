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
ms.openlocfilehash: e2168c167c89f989f70a10d5832e70c93a8f90f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529892"
---
# <a name="assembly-placement"></a><span data-ttu-id="b3a1a-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="b3a1a-102">Assembly Placement</span></span>
<span data-ttu-id="b3a1a-103">Pro většinu aplikací rozhraní .NET Framework můžete vyhledat sestavení, které tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sdílená sestavení).</span><span class="sxs-lookup"><span data-stu-id="b3a1a-103">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="b3a1a-104">Můžete přepsat, kde modul common language runtime vyhledá sestavení s použitím [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-104">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="b3a1a-105">Pokud sestavení nemá silný název, umístění zadaného pomocí [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) je omezen na adresáři aplikace nebo podadresáře.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-105">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="b3a1a-106">Pokud sestavení se silným názvem, [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) zadat jakékoli umístění v počítači nebo v síti.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-106">If the assembly has a strong name, the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="b3a1a-107">Podobně jako pravidla platí pro vyhledání sestavení, když pracujete s nespravovaným kódem nebo definiční aplikace modelu COM: Pokud sestavení budou sdílet více aplikací, je nutné ji nainstalovat do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-107">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="b3a1a-108">Sestavení, které používá s nespravovaným kódem musí být exportován jako knihovnu typů a zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-108">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="b3a1a-109">Sestavení používá zprostředkovatele komunikace s objekty COM musí být zaregistrovaný v katalogu, i když v některých případech tato registrace probíhá automaticky.</span><span class="sxs-lookup"><span data-stu-id="b3a1a-109">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a1a-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3a1a-110">See also</span></span>
- [<span data-ttu-id="b3a1a-111">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="b3a1a-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b3a1a-112">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="b3a1a-112">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="b3a1a-113">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="b3a1a-113">Interoperating with unmanaged code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="b3a1a-114">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="b3a1a-114">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
