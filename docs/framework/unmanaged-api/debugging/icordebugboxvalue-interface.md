---
title: ICorDebugBoxValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: 1ec54f4fe36aaf38d7c0ce0586733729bd2fddea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784471"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="3de1d-102">ICorDebugBoxValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3de1d-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="3de1d-103">Podtřída "ICorDebugHeapValue", která představuje zabalený objekt třídy hodnot.</span><span class="sxs-lookup"><span data-stu-id="3de1d-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3de1d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3de1d-104">Methods</span></span>  
  
|<span data-ttu-id="3de1d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3de1d-105">Method</span></span>|<span data-ttu-id="3de1d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3de1d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3de1d-107">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="3de1d-107">GetObject Method</span></span>](icordebugboxvalue-getobject-method.md)|<span data-ttu-id="3de1d-108">Načte ukazatel rozhraní do zabalené instance "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="3de1d-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3de1d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3de1d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3de1d-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3de1d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de1d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3de1d-111">Requirements</span></span>  
 <span data-ttu-id="3de1d-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de1d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de1d-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3de1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3de1d-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3de1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3de1d-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de1d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3de1d-116">See also</span></span>

- [<span data-ttu-id="3de1d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3de1d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
