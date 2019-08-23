---
title: ICorDebugInternalFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9764cdcd07a09f5192a8f43b9baa5be40305c40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910158"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="0ebca-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ebca-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="0ebca-103">Představuje interní rámec modulu runtime v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0ebca-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="0ebca-104">Toto rozhraní je podtřídou rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0ebca-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ebca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0ebca-105">Methods</span></span>  
  
|<span data-ttu-id="0ebca-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ebca-106">Method</span></span>|<span data-ttu-id="0ebca-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0ebca-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ebca-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="0ebca-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="0ebca-109">Získá typ tohoto interního rámce.</span><span class="sxs-lookup"><span data-stu-id="0ebca-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebca-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ebca-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ebca-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0ebca-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebca-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ebca-112">Requirements</span></span>  
 <span data-ttu-id="0ebca-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebca-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebca-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ebca-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebca-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebca-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebca-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebca-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebca-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ebca-117">See also</span></span>

- [<span data-ttu-id="0ebca-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ebca-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
