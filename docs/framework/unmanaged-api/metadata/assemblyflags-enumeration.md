---
title: "AssemblyFlags – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91760b6d16b663257bf3d89915da3bd88b3411bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="b755b-102">AssemblyFlags – výčet</span><span class="sxs-lookup"><span data-stu-id="b755b-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="b755b-103">Obsahuje hodnoty, které popisují funkce běhové sestavení.</span><span class="sxs-lookup"><span data-stu-id="b755b-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b755b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b755b-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b755b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b755b-105">Members</span></span>  
  
|<span data-ttu-id="b755b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b755b-106">Member</span></span>|<span data-ttu-id="b755b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b755b-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="b755b-108">Určuje, že jsou definice exportovaný typu implicitní v souborech, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="b755b-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b755b-109">V rozhraní .NET Framework verze 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="b755b-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="b755b-110">Určuje, že jsou definice prostředků implicitní v souborech, které tvoří sestavení.</span><span class="sxs-lookup"><span data-stu-id="b755b-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="b755b-111">V rozhraní .NET Framework 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="b755b-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="b755b-112">Určuje, že sestavení nelze provést s jinými verzemi, pokud běží ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="b755b-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="b755b-113">Určuje, že sestavení nelze provést s jinými verzemi spuštěné ve stejném procesu.</span><span class="sxs-lookup"><span data-stu-id="b755b-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="b755b-114">Určuje, že sestavení nelze provést s jinými verzemi, pokud jsou spuštěné na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="b755b-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b755b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b755b-115">Remarks</span></span>  
 <span data-ttu-id="b755b-116">Hodnoty mezi 0x0010 a 0x0070, včetně, se používají k popisu funkce kompatibility vedle sebe odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="b755b-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="b755b-117">Pokud nejsou nastavené žádné z těchto hodnot, sestavení se považuje za kompatibilní vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="b755b-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b755b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b755b-118">Requirements</span></span>  
 <span data-ttu-id="b755b-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b755b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b755b-120">**Záhlaví:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b755b-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="b755b-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b755b-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b755b-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b755b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b755b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b755b-123">See Also</span></span>  
 [<span data-ttu-id="b755b-124">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="b755b-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="b755b-125">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b755b-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
