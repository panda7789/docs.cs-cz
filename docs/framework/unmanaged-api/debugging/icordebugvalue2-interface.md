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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0925cf217afafe57abf82cf51a77b1992bad5152
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966833"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="894b2-102">ICorDebugValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="894b2-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="894b2-103">Rozšiřuje rozhraní "ICorDebugValue", aby poskytoval podporu pro objekty "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="894b2-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="894b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="894b2-104">Methods</span></span>  
  
|<span data-ttu-id="894b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="894b2-105">Method</span></span>|<span data-ttu-id="894b2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="894b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="894b2-107">GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="894b2-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="894b2-108">Získá ukazatel rozhraní na `ICorDebugType` objekt, který <xref:System.Type> představuje tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="894b2-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="894b2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="894b2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="894b2-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="894b2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="894b2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="894b2-111">Requirements</span></span>  
 <span data-ttu-id="894b2-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="894b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="894b2-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="894b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="894b2-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="894b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="894b2-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894b2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="894b2-116">See also</span></span>

- [<span data-ttu-id="894b2-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="894b2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="894b2-118">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="894b2-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
