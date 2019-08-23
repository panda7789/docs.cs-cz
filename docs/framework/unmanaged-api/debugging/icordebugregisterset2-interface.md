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
ms.openlocfilehash: 95e8ad1ddce57252b7af3c7d72e8f8eb7bdb76b0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935095"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="2eb8a-102">ICorDebugRegisterSet2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2eb8a-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="2eb8a-103">Rozšiřuje možnosti rozhraní [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pro hardwarové platformy, které mají více než 64 registrů.</span><span class="sxs-lookup"><span data-stu-id="2eb8a-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2eb8a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2eb8a-104">Methods</span></span>  
  
|<span data-ttu-id="2eb8a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2eb8a-105">Method</span></span>|<span data-ttu-id="2eb8a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2eb8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2eb8a-107">GetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="2eb8a-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="2eb8a-108">Získá hodnotu každého registru (na počítači, který právě spouští kód), který je určen bitovou maskou.</span><span class="sxs-lookup"><span data-stu-id="2eb8a-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="2eb8a-109">GetRegistersAvailable – metoda</span><span class="sxs-lookup"><span data-stu-id="2eb8a-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="2eb8a-110">Získá pole bajtů, které poskytuje rastrový obrázek dostupných registrů.</span><span class="sxs-lookup"><span data-stu-id="2eb8a-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="2eb8a-111">SetRegisters – metoda</span><span class="sxs-lookup"><span data-stu-id="2eb8a-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="2eb8a-112">Není implementováno v .NET Framework verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="2eb8a-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2eb8a-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2eb8a-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2eb8a-114">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2eb8a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2eb8a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2eb8a-115">Requirements</span></span>  
 <span data-ttu-id="2eb8a-116">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2eb8a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2eb8a-117">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2eb8a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2eb8a-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2eb8a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2eb8a-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2eb8a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb8a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2eb8a-120">See also</span></span>

- [<span data-ttu-id="2eb8a-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2eb8a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2eb8a-122">ICorDebugRegisterSet – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2eb8a-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
