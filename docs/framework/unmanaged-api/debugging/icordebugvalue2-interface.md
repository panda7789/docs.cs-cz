---
title: ICorDebugValue2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: ab5adabe868c245ed7a773d9b4206b25d9e9a4f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140242"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="280fb-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="280fb-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="280fb-103">Rozšiřuje rozhraní "ICorDebugValue", aby poskytoval podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="280fb-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="280fb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="280fb-104">Methods</span></span>  
  
|<span data-ttu-id="280fb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="280fb-105">Method</span></span>|<span data-ttu-id="280fb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="280fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="280fb-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="280fb-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="280fb-108">Získá ukazatel rozhraní na objekt `ICorDebugType`, který představuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="280fb-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="280fb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="280fb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="280fb-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="280fb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="280fb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="280fb-111">Requirements</span></span>  
 <span data-ttu-id="280fb-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="280fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="280fb-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="280fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="280fb-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="280fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="280fb-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="280fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="280fb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="280fb-116">See also</span></span>

- [<span data-ttu-id="280fb-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="280fb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="280fb-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="280fb-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
