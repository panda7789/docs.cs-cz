---
title: "CorDebugGCType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGCType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGCType
helpviewer_keywords: CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 14d6f28c2e5fa356c7f406ffb4c2787f0ace500a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="d6c84-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="d6c84-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="d6c84-103">Určuje, zda má systém uvolňování běží na pracovní stanici nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="d6c84-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6c84-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6c84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6c84-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="d6c84-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d6c84-106">Members</span></span>  
  
|<span data-ttu-id="d6c84-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="d6c84-107">Member name</span></span>|<span data-ttu-id="d6c84-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d6c84-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="d6c84-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="d6c84-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="d6c84-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="d6c84-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6c84-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6c84-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c84-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6c84-112">Requirements</span></span>  
 <span data-ttu-id="d6c84-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c84-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6c84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6c84-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c84-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c84-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6c84-117">See Also</span></span>  
 [<span data-ttu-id="d6c84-118">Ladění výčtů</span><span class="sxs-lookup"><span data-stu-id="d6c84-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
