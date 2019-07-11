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
ms.openlocfilehash: f101fe2a84a26efb23f57bac3aaf4f0e64a4d36c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740027"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="0480d-102">CorDebugGCType – výčet</span><span class="sxs-lookup"><span data-stu-id="0480d-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="0480d-103">Určuje, zda systému uvolňování paměti běží na serveru nebo pracovní stanice.</span><span class="sxs-lookup"><span data-stu-id="0480d-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0480d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0480d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
## <a name="parameters"></a><span data-ttu-id="0480d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0480d-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="0480d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="0480d-106">Members</span></span>  
  
|<span data-ttu-id="0480d-107">Název členu</span><span class="sxs-lookup"><span data-stu-id="0480d-107">Member name</span></span>|<span data-ttu-id="0480d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="0480d-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="0480d-109">Uvolňování paměti běží na pracovní stanici.</span><span class="sxs-lookup"><span data-stu-id="0480d-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="0480d-110">Uvolňování paměti běží na serveru.</span><span class="sxs-lookup"><span data-stu-id="0480d-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0480d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0480d-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0480d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0480d-112">Requirements</span></span>  
 <span data-ttu-id="0480d-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0480d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0480d-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0480d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0480d-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0480d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0480d-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0480d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0480d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0480d-117">See also</span></span>

- [<span data-ttu-id="0480d-118">Výčty pro ladění</span><span class="sxs-lookup"><span data-stu-id="0480d-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
