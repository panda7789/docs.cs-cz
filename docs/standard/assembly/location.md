---
title: Umístění sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733123"
---
# <a name="assembly-location"></a><span data-ttu-id="7a100-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="7a100-102">Assembly location</span></span>
<span data-ttu-id="7a100-103">Umístění sestavení Určuje, zda se modul CLR (Common Language Runtime) může při odkazování najít a může také určit, zda může být sestavení sdíleno s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="7a100-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="7a100-104">Sestavení můžete nasadit v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="7a100-104">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="7a100-105">Adresář nebo podadresáře aplikace</span><span class="sxs-lookup"><span data-stu-id="7a100-105">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="7a100-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a100-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="7a100-107">Podadresáře kořenového adresáře aplikace může být založen na jazyku nebo jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="7a100-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="7a100-108">Pokud sestavení obsahuje informace v atributu Culture, musí být v podadresáři v adresáři aplikace s názvem této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="7a100-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="7a100-109">Globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="7a100-109">The global assembly cache.</span></span>

     <span data-ttu-id="7a100-110">Jedná se o mezipaměť kódu v celém počítači, která je nainstalována bez ohledu na to, kde je nainstalován modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="7a100-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="7a100-111">Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, je nutné jej nasadit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="7a100-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="7a100-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a100-112">On an HTTP server.</span></span>

     <span data-ttu-id="7a100-113">Sestavení nasazené na serveru HTTP musí mít silný název; odkazujete na sestavení v oddílu základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a100-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a100-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a100-114">See also</span></span>

- [<span data-ttu-id="7a100-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="7a100-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="7a100-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="7a100-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="7a100-117">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7a100-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
