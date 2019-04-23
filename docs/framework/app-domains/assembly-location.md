---
title: Umístění sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c638531bd54f14c7e4b04a093deaec729db404ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129633"
---
# <a name="assembly-location"></a><span data-ttu-id="c7a4c-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="c7a4c-102">Assembly Location</span></span>
<span data-ttu-id="c7a4c-103">Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a můžete také určit, zda sestavení lze sdílet s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="c7a4c-104">Můžete nasazovat sestavení v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="c7a4c-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="c7a4c-105">Adresář nebo podadresáře vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="c7a4c-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="c7a4c-107">Podadresáře kořenový adresář aplikace může být založen na jazyk nebo jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="c7a4c-108">Pokud sestavení využívá informace v atributu jazykové verze, musí být v podadresáři adresáře aplikace s názvem danou jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="c7a4c-109">Globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="c7a4c-110">Toto je mezipaměť kódu celého stroje, který je nainstalován všude, kde je nainstalován modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="c7a4c-111">Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ho do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="c7a4c-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="c7a4c-113">Nasazení na HTTP server sestavení musí mít silný název; odkazovat na sestavení v části základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="c7a4c-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a4c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7a4c-114">See also</span></span>

- [<span data-ttu-id="c7a4c-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="c7a4c-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="c7a4c-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="c7a4c-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="c7a4c-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="c7a4c-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c7a4c-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="c7a4c-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
