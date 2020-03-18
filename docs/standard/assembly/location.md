---
title: Umístění sestavení
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 0b84aba749625f0f86027cd9d09a5e9a2229a3f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73733123"
---
# <a name="assembly-location"></a><span data-ttu-id="9c124-102">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="9c124-102">Assembly location</span></span>
<span data-ttu-id="9c124-103">Umístění sestavení určuje, zda jej běžný jazyk runtime může vyhledat při odkazování a může také určit, zda lze sestavení sdílet s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="9c124-103">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="9c124-104">Sestavení můžete nasadit v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="9c124-104">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="9c124-105">Adresář nebo podadresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c124-105">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="9c124-106">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c124-106">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="9c124-107">Podadresáře kořenového adresáře aplikace mohou být založeny na jazyku nebo jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="9c124-107">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="9c124-108">Pokud má sestavení informace v atributu jazykové verze, musí být v podadresáři pod adresářem aplikace s názvem této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="9c124-108">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="9c124-109">Globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c124-109">The global assembly cache.</span></span>

     <span data-ttu-id="9c124-110">Jedná se o mezipaměť kódu celého počítače, která je nainstalována všude tam, kde je nainstalován a) běžný jazyk runtime.</span><span class="sxs-lookup"><span data-stu-id="9c124-110">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="9c124-111">Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, měli byste jej nasadit do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="9c124-111">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="9c124-112">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="9c124-112">On an HTTP server.</span></span>

     <span data-ttu-id="9c124-113">Sestavení nasazené na serveru HTTP musí mít silný název. přejdete na sestavení v části základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c124-113">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c124-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c124-114">See also</span></span>

- [<span data-ttu-id="9c124-115">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="9c124-115">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="9c124-116">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="9c124-116">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="9c124-117">Jak runtime vyhledá sestavení</span><span class="sxs-lookup"><span data-stu-id="9c124-117">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
