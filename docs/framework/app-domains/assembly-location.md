---
title: "Umístění sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96b3105dcd1eaf6d95269d05518e6892b42a638f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-location"></a><span data-ttu-id="1165f-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="1165f-102">Assembly Location</span></span>
<span data-ttu-id="1165f-103">Umístění sestavení určuje, zda modul common language runtime najít při odkazuje a také dokáže určit, zda je sestavení je možné sdílet s ostatních sestavení.</span><span class="sxs-lookup"><span data-stu-id="1165f-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="1165f-104">Můžete nasadit sestavení v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="1165f-104">You can deploy an assembly in the following locations:</span></span>  
  
-   <span data-ttu-id="1165f-105">Adresář nebo podadresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="1165f-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="1165f-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="1165f-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="1165f-107">Podadresáře kořenovému adresáři aplikace může být založen na jazyk nebo jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="1165f-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="1165f-108">Pokud má sestavení informace v atributu jazykovou verzi, musí být v podadresáři v adresáři aplikace s názvem tuto jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="1165f-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
-   <span data-ttu-id="1165f-109">Globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="1165f-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="1165f-110">Jde o mezipaměť strojový kód, který je nainstalován, kde je nainstalován modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1165f-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="1165f-111">Ve většině případů Pokud máte v úmyslu sdílení sestavení s více aplikacemi, měli byste nasadit ji do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="1165f-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="1165f-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="1165f-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="1165f-113">Sestavení nasazeno na HTTP serveru musí mít silný název; Nasměrujte sestavení v sekci codebase konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1165f-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1165f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1165f-114">See Also</span></span>  
 [<span data-ttu-id="1165f-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="1165f-115">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="1165f-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="1165f-116">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)  
 [<span data-ttu-id="1165f-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="1165f-117">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="1165f-118">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="1165f-118">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
