---
title: "COR_VERSION – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b527cb9175315af98a9ad4e9be06d459ad6e188e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="22fcf-102">COR_VERSION – struktura</span><span class="sxs-lookup"><span data-stu-id="22fcf-102">COR_VERSION Structure</span></span>
<span data-ttu-id="22fcf-103">Ukládá číslo standardní sestávající ze čtyř částí verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="22fcf-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22fcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22fcf-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="22fcf-105">Členové</span><span class="sxs-lookup"><span data-stu-id="22fcf-105">Members</span></span>  
  
|<span data-ttu-id="22fcf-106">Člen</span><span class="sxs-lookup"><span data-stu-id="22fcf-106">Member</span></span>|<span data-ttu-id="22fcf-107">Popis</span><span class="sxs-lookup"><span data-stu-id="22fcf-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="22fcf-108">Hlavní číslo verze.</span><span class="sxs-lookup"><span data-stu-id="22fcf-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="22fcf-109">Vedlejší číslo verze.</span><span class="sxs-lookup"><span data-stu-id="22fcf-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="22fcf-110">Číslo sestavení.</span><span class="sxs-lookup"><span data-stu-id="22fcf-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="22fcf-111">Číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="22fcf-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22fcf-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22fcf-112">Remarks</span></span>  
 <span data-ttu-id="22fcf-113">Pokud je číslo verze 1.0.3705.288, je hlavní číslo verze 1, 0 je číslo podverze, 3705 je číslo sestavení a 288 je číslo dílčí sestavení.</span><span class="sxs-lookup"><span data-stu-id="22fcf-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22fcf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22fcf-114">Requirements</span></span>  
 <span data-ttu-id="22fcf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22fcf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22fcf-116">**Záhlaví:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="22fcf-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="22fcf-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22fcf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22fcf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22fcf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22fcf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="22fcf-119">See Also</span></span>  
 [<span data-ttu-id="22fcf-120">Struktury pro ladění</span><span class="sxs-lookup"><span data-stu-id="22fcf-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="22fcf-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="22fcf-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
