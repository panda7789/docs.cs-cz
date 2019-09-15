---
title: Umístění sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6427f7d005c43ef9e83387e865f71009b683a7c4
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973178"
---
# <a name="assembly-location"></a><span data-ttu-id="421ef-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="421ef-102">Assembly location</span></span>
<span data-ttu-id="421ef-103">Umístění sestavení Určuje, zda se modul CLR (Common Language Runtime) může při odkazování najít a může také určit, zda může být sestavení sdíleno s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="421ef-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="421ef-104">Sestavení můžete nasadit v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="421ef-104">You can deploy an assembly in the following locations:</span></span>  
  
- <span data-ttu-id="421ef-105">Adresář nebo podadresáře aplikace</span><span class="sxs-lookup"><span data-stu-id="421ef-105">The application's directory or subdirectories.</span></span>  
  
     <span data-ttu-id="421ef-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="421ef-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="421ef-107">Podadresáře kořenového adresáře aplikace může být založen na jazyku nebo jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="421ef-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="421ef-108">Pokud sestavení obsahuje informace v atributu Culture, musí být v podadresáři v adresáři aplikace s názvem této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="421ef-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>  
  
- <span data-ttu-id="421ef-109">Globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="421ef-109">The global assembly cache.</span></span>  
  
     <span data-ttu-id="421ef-110">Jedná se o mezipaměť kódu v celém počítači, která je nainstalována bez ohledu na to, kde je nainstalován modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="421ef-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="421ef-111">Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, je nutné jej nasadit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="421ef-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>  
  
- <span data-ttu-id="421ef-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="421ef-112">On an HTTP server.</span></span>  
  
     <span data-ttu-id="421ef-113">Sestavení nasazené na serveru HTTP musí mít silný název; odkazujete na sestavení v oddílu základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="421ef-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="421ef-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="421ef-114">See also</span></span>

- [<span data-ttu-id="421ef-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="421ef-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="421ef-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="421ef-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="421ef-117">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="421ef-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="421ef-118">Program se sestaveními</span><span class="sxs-lookup"><span data-stu-id="421ef-118">Program with assemblies</span></span>](program.md)
