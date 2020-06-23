---
title: Umístění sestavení
description: Přečtěte si pokyny pro umístění sestavení .NET v adresářích (například v globální mezipaměti sestavení nebo v adresáři nebo v adresáři aplikace).
ms.date: 03/30/2017
helpviewer_keywords:
- <codeBase> element
- locating assemblies
- assemblies [.NET Framework], placement
- assemblies [.NET Framework], location
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
ms.openlocfilehash: 3106f6f01229057725cbc2e8e689a4e2247f95e6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104961"
---
# <a name="assembly-placement"></a><span data-ttu-id="9a788-103">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="9a788-103">Assembly Placement</span></span>
<span data-ttu-id="9a788-104">Pro většinu .NET Frameworkch aplikací naleznete sestavení, která tvoří aplikaci v adresáři aplikace, v podadresáři adresáře aplikace nebo v globální mezipaměti sestavení (Pokud je sestavení sdíleno).</span><span class="sxs-lookup"><span data-stu-id="9a788-104">For most .NET Framework applications, you locate assemblies that make up an application in the application's directory, in a subdirectory of the application's directory, or in the global assembly cache (if the assembly is shared).</span></span> <span data-ttu-id="9a788-105">Můžete přepsat, kde modul CLR (Common Language Runtime) hledá sestavení pomocí [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9a788-105">You can override where the common language runtime looks for an assembly by using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) in a configuration file.</span></span> <span data-ttu-id="9a788-106">Pokud sestavení nemá silný název, umístění zadané pomocí [ \<codeBase> elementu](../configure-apps/file-schema/runtime/codebase-element.md) je omezeno na adresář aplikace nebo na podadresář.</span><span class="sxs-lookup"><span data-stu-id="9a788-106">If the assembly does not have a strong name, the location specified using the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) is restricted to the application directory or a subdirectory.</span></span> <span data-ttu-id="9a788-107">Pokud má sestavení silný název, [ \<codeBase> element](../configure-apps/file-schema/runtime/codebase-element.md) může určovat libovolné umístění v počítači nebo v síti.</span><span class="sxs-lookup"><span data-stu-id="9a788-107">If the assembly has a strong name, the [\<codeBase> Element](../configure-apps/file-schema/runtime/codebase-element.md) can specify any location on the computer or on a network.</span></span>  
  
 <span data-ttu-id="9a788-108">Podobná pravidla se vztahují na lokalizaci sestavení při práci s nespravovaným kódem nebo aplikacemi COM interop: Pokud bude sestavení sdíleno více aplikacemi, měla by být nainstalována do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="9a788-108">Similar rules apply to locating assemblies when working with unmanaged code or COM interop applications: if the assembly will be shared by multiple applications, it should be installed into the global assembly cache.</span></span> <span data-ttu-id="9a788-109">Sestavení použitá s nespravovaným kódem musí být exportována jako knihovna typů a zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="9a788-109">Assemblies used with unmanaged code must be exported as a type library and registered.</span></span> <span data-ttu-id="9a788-110">Sestavení používaná zprostředkovatelem komunikace s objekty COM musí být registrována v katalogu, i když v některých případech tato registrace probíhá automaticky.</span><span class="sxs-lookup"><span data-stu-id="9a788-110">Assemblies used by COM interop must be registered in the catalog, although in some cases this registration occurs automatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a788-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a788-111">See also</span></span>

- [<span data-ttu-id="9a788-112">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="9a788-112">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9a788-113">Konfigurace aplikací</span><span class="sxs-lookup"><span data-stu-id="9a788-113">Configuring Apps</span></span>](../configure-apps/index.md)
- [<span data-ttu-id="9a788-114">Spolupráce s nespravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="9a788-114">Interoperating with unmanaged code</span></span>](../interop/index.md)
- [<span data-ttu-id="9a788-115">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="9a788-115">Assemblies in .NET</span></span>](index.md)
