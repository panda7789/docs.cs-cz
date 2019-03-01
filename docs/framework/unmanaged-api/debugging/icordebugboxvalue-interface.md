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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7238574334b599c7922693c7e9a476a51785491
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967320"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="231a4-102">ICorDebugBoxValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="231a4-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="231a4-103">Podtřída "ICorDebugHeapValue" představující objektu třídy zabalených hodnot.</span><span class="sxs-lookup"><span data-stu-id="231a4-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="231a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="231a4-104">Methods</span></span>  
  
|<span data-ttu-id="231a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="231a4-105">Method</span></span>|<span data-ttu-id="231a4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="231a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="231a4-107">GetObject – metoda</span><span class="sxs-lookup"><span data-stu-id="231a4-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="231a4-108">Získá ukazatel rozhraní k instanci zabalený "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="231a4-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="231a4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="231a4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="231a4-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="231a4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="231a4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="231a4-111">Requirements</span></span>  
 <span data-ttu-id="231a4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="231a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="231a4-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="231a4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="231a4-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="231a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="231a4-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="231a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="231a4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="231a4-116">See also</span></span>
- [<span data-ttu-id="231a4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="231a4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
