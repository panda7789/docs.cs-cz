---
title: Umístění sestavení
description: Umístění sestavení .NET určuje, jak ho CLR najde a zda jej lze sdílet s jinými sestaveními.
ms.date: 08/20/2019
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
ms.openlocfilehash: 7ab3804b14b586e1430d654f4da32a310bcb6cc9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379899"
---
# <a name="assembly-location"></a><span data-ttu-id="f1fa7-103">Umístění sestavení</span><span class="sxs-lookup"><span data-stu-id="f1fa7-103">Assembly location</span></span>
<span data-ttu-id="f1fa7-104">Umístění sestavení Určuje, zda se modul CLR (Common Language Runtime) může při odkazování najít a může také určit, zda může být sestavení sdíleno s jinými sestaveními.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-104">An assembly's location determines whether the common language runtime can locate it when referenced, and can also determine whether the assembly can be shared with other assemblies.</span></span> <span data-ttu-id="f1fa7-105">Sestavení můžete nasadit v následujících umístěních:</span><span class="sxs-lookup"><span data-stu-id="f1fa7-105">You can deploy an assembly in the following locations:</span></span>

- <span data-ttu-id="f1fa7-106">Adresář nebo podadresáře aplikace</span><span class="sxs-lookup"><span data-stu-id="f1fa7-106">The application's directory or subdirectories.</span></span>

     <span data-ttu-id="f1fa7-107">Toto je nejběžnější umístění pro nasazení sestavení.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-107">This is the most common location for deploying an assembly.</span></span> <span data-ttu-id="f1fa7-108">Podadresáře kořenového adresáře aplikace může být založen na jazyku nebo jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-108">The subdirectories of an application's root directory can be based on language or culture.</span></span> <span data-ttu-id="f1fa7-109">Pokud sestavení obsahuje informace v atributu Culture, musí být v podadresáři v adresáři aplikace s názvem této jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-109">If an assembly has information in the culture attribute, it must be in a subdirectory under the application directory with that culture's name.</span></span>

- <span data-ttu-id="f1fa7-110">Globální mezipaměť sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="f1fa7-110">The global assembly cache.</span></span>

     <span data-ttu-id="f1fa7-111">Jedná se o mezipaměť kódu v celém počítači, která je nainstalována bez ohledu na to, kde je nainstalován modul CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="f1fa7-111">This is a machine-wide code cache that is installed wherever the common language runtime is installed.</span></span> <span data-ttu-id="f1fa7-112">Ve většině případů, pokud máte v úmyslu sdílet sestavení s více aplikacemi, je nutné jej nasadit do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="f1fa7-112">In most cases, if you intend to share an assembly with multiple applications, you should deploy it into the global assembly cache.</span></span>

- <span data-ttu-id="f1fa7-113">Na serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-113">On an HTTP server.</span></span>

     <span data-ttu-id="f1fa7-114">Sestavení nasazené na serveru HTTP musí mít silný název; odkazujete na sestavení v oddílu základu kódu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1fa7-114">An assembly deployed on an HTTP server must have a strong name; you point to the assembly in the codebase section of the application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1fa7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1fa7-115">See also</span></span>

- [<span data-ttu-id="f1fa7-116">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="f1fa7-116">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="f1fa7-117">Globální mezipaměť sestavení</span><span class="sxs-lookup"><span data-stu-id="f1fa7-117">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="f1fa7-118">Způsob, jakým modul runtime vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="f1fa7-118">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
