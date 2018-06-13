---
title: AssemblyFlags – výčet
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444903"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="9e920-102">AssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="9e920-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="9e920-103">Obsahuje hodnoty, které popisují funkce běhové sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e920-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e920-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e920-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9e920-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9e920-105">Members</span></span>  
  
|<span data-ttu-id="9e920-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9e920-106">Member</span></span>|<span data-ttu-id="9e920-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9e920-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="9e920-108">Určuje, že jsou definice exportovaný typu implicitní v souborech, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e920-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="9e920-109">V rozhraní .NET Framework verze 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="9e920-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="9e920-110">Určuje, že jsou definice prostředků implicitní v souborech, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e920-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="9e920-111">V rozhraní .NET Framework 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="9e920-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="9e920-112">Určuje, že sestavení nelze provést s jinými verzemi, pokud běží ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e920-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="9e920-113">Určuje, že sestavení nelze provést s jinými verzemi spuštěné ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="9e920-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="9e920-114">Určuje, že sestavení nelze provést s jinými verzemi, pokud jsou spuštěné na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="9e920-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e920-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e920-115">Remarks</span></span>  
 <span data-ttu-id="9e920-116">Hodnoty mezi 0x0010 a 0x0070, včetně, se používají k popisu funkce kompatibility vedle sebe odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="9e920-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="9e920-117">Pokud nejsou nastavené žádné z těchto hodnot, sestavení se považuje za kompatibilní vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="9e920-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e920-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e920-118">Requirements</span></span>  
 <span data-ttu-id="9e920-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e920-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e920-120">**Záhlaví:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e920-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="9e920-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e920-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9e920-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e920-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e920-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e920-123">See Also</span></span>  
 [<span data-ttu-id="9e920-124">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9e920-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="9e920-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e920-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
