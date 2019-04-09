---
title: CorDebugGCType – výčet
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 315d6dd522f3c6be2d36b1eb411d9f471350df60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182920"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="03240-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="03240-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="03240-103">Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="03240-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03240-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03240-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="03240-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03240-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="03240-106">Členové</span><span class="sxs-lookup"><span data-stu-id="03240-106">Members</span></span>  
  
|<span data-ttu-id="03240-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="03240-107">Member name</span></span>|<span data-ttu-id="03240-108">Popis</span><span class="sxs-lookup"><span data-stu-id="03240-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="03240-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="03240-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="03240-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="03240-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03240-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03240-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03240-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03240-112">Requirements</span></span>  
 <span data-ttu-id="03240-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03240-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03240-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="03240-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03240-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03240-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="03240-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="03240-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03240-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03240-117">See also</span></span>

- [<span data-ttu-id="03240-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="03240-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
