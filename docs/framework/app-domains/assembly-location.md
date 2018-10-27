---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19c4b030e8b44bed5377827d016127b4a574f5ee
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183747"
---
# <a name="assembly-location"></a><span data-ttu-id="0364d-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="0364d-102">Assembly Location</span></span>
<span data-ttu-id="0364d-103">Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a můžete také určit, zda sestavení lze sdílet s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="0364d-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="0364d-104">Můžete nasazovat sestavení v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="0364d-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="0364d-105">Adresář nebo podadresáře vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="0364d-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="0364d-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="0364d-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="0364d-107">Podadresáře kořenový adresář aplikace může být založen na jazyk nebo jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="0364d-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="0364d-108">Pokud sestavení využívá informace v atributu jazykové verze, musí být v podadresáři adresáře aplikace s názvem danou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="0364d-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="0364d-109">Globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0364d-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="0364d-110">Toto je mezipaměť kódu celého stroje, který je nainstalován všude, kde je nainstalován modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0364d-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="0364d-111">Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ho do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0364d-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="0364d-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="0364d-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="0364d-113">Nasazení na HTTP server sestavení musí mít silný název; odkazovat na sestavení v části základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0364d-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0364d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0364d-114">See Also</span></span>  
- [<span data-ttu-id="0364d-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="0364d-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="0364d-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="0364d-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
- [<span data-ttu-id="0364d-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="0364d-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="0364d-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="0364d-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
