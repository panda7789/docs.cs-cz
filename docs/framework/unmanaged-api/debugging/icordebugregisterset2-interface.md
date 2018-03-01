---
title: "ICorDebugRegisterSet2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f01a1d291216fca84b70fce8389efee3d7e2dd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="2ff5f-102">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff5f-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="2ff5f-103">Rozšiřuje možnosti [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) rozhraní pro hardwarových platforem, které mají víc než 64 Registry.</span><span class="sxs-lookup"><span data-stu-id="2ff5f-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ff5f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2ff5f-104">Methods</span></span>  
  
|<span data-ttu-id="2ff5f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ff5f-105">Method</span></span>|<span data-ttu-id="2ff5f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2ff5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ff5f-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff5f-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="2ff5f-108">Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.</span><span class="sxs-lookup"><span data-stu-id="2ff5f-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="2ff5f-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff5f-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="2ff5f-110">Získá pole bajtů, které poskytuje rastrový obrázek k dispozici registrů.</span><span class="sxs-lookup"><span data-stu-id="2ff5f-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="2ff5f-111">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="2ff5f-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="2ff5f-112">Není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="2ff5f-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ff5f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ff5f-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff5f-114">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2ff5f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ff5f-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ff5f-115">Requirements</span></span>  
 <span data-ttu-id="2ff5f-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ff5f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ff5f-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ff5f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ff5f-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ff5f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ff5f-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ff5f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff5f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ff5f-120">See Also</span></span>  
 [<span data-ttu-id="2ff5f-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2ff5f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2ff5f-122">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ff5f-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
