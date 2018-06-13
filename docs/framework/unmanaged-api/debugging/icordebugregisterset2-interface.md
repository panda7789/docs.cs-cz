---
title: ICorDebugRegisterSet2 – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f4947a9b6c0e3fd87ee474111f143d273c1d7b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422788"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="29433-102">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29433-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="29433-103">Rozšiřuje možnosti [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) rozhraní pro hardwarových platforem, které mají víc než 64 Registry.</span><span class="sxs-lookup"><span data-stu-id="29433-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29433-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29433-104">Methods</span></span>  
  
|<span data-ttu-id="29433-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29433-105">Method</span></span>|<span data-ttu-id="29433-106">Popis</span><span class="sxs-lookup"><span data-stu-id="29433-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29433-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="29433-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="29433-108">Získá hodnotu každý registrace (v počítači, který je aktuálně provádění kódu), který je určen podle bit masky.</span><span class="sxs-lookup"><span data-stu-id="29433-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="29433-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="29433-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="29433-110">Získá pole bajtů, které poskytuje rastrový obrázek k dispozici registrů.</span><span class="sxs-lookup"><span data-stu-id="29433-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="29433-111">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="29433-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="29433-112">Není implementováno v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="29433-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29433-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29433-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29433-114">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="29433-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29433-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29433-115">Requirements</span></span>  
 <span data-ttu-id="29433-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29433-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29433-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29433-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29433-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29433-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29433-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29433-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29433-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="29433-120">See Also</span></span>  
 [<span data-ttu-id="29433-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="29433-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="29433-122">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29433-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
