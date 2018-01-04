---
title: "CorPEKind – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPEKind
helpviewer_keywords: CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612c71db092e7a3474d262c1d601335a5f416791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corpekind-enumeration"></a><span data-ttu-id="9cddd-102">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="9cddd-102">CorPEKind Enumeration</span></span>
<span data-ttu-id="9cddd-103">Obsahuje hodnoty, které popisují souboru přenosné spustitelný soubor (PE), jak ho vrátila volání [imetadataimport2::getpekind –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span><span class="sxs-lookup"><span data-stu-id="9cddd-103">Contains values that describe a portable executable (PE) file, as returned from a call to [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cddd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9cddd-104">Syntax</span></span>  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a><span data-ttu-id="9cddd-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9cddd-105">Members</span></span>  
  
|<span data-ttu-id="9cddd-106">Člen</span><span class="sxs-lookup"><span data-stu-id="9cddd-106">Member</span></span>|<span data-ttu-id="9cddd-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9cddd-107">Description</span></span>|  
|------------|-----------------|  
|`peNot`|<span data-ttu-id="9cddd-108">Označuje, že se nejedná o soubor PE.</span><span class="sxs-lookup"><span data-stu-id="9cddd-108">Indicates that this is not a PE file.</span></span>|  
|`peILOnly`|<span data-ttu-id="9cddd-109">Označuje, že tento soubor PE obsahuje pouze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="9cddd-109">Indicates that this PE file contains only managed code.</span></span>|  
|`pe32BitRequired`|<span data-ttu-id="9cddd-110">Označuje, že tento soubor PE provádí volání Win32.</span><span class="sxs-lookup"><span data-stu-id="9cddd-110">Indicates that this PE file makes Win32 calls.</span></span>|  
|`pe32Plus`|<span data-ttu-id="9cddd-111">Udává, že tento PE soubor spouští na 64bitové platformě.</span><span class="sxs-lookup"><span data-stu-id="9cddd-111">Indicates that this PE file runs on a 64-bit platform.</span></span>|  
|`pe32Unmanaged`|<span data-ttu-id="9cddd-112">Označuje, že je tento soubor PE nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="9cddd-112">Indicates that this PE file is native code.</span></span>|  
|<span data-ttu-id="9cddd-113">pe32BitPreferred</span><span class="sxs-lookup"><span data-stu-id="9cddd-113">pe32BitPreferred</span></span>|<span data-ttu-id="9cddd-114">Označuje, že tento soubor PE je platforma jazykově neutrální a upřednostní pro otevření v prostředí s 32-bit.</span><span class="sxs-lookup"><span data-stu-id="9cddd-114">Indicates that this PE file is platform-neutral and prefers to be loaded in a 32-bit environment.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cddd-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cddd-115">Remarks</span></span>  
 <span data-ttu-id="9cddd-116">Tyto hodnoty lze v bitové kombinace.</span><span class="sxs-lookup"><span data-stu-id="9cddd-116">These values can be used in bitwise combinations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cddd-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cddd-117">Requirements</span></span>  
 <span data-ttu-id="9cddd-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cddd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cddd-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9cddd-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9cddd-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cddd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cddd-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cddd-121">See Also</span></span>  
 [<span data-ttu-id="9cddd-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="9cddd-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
