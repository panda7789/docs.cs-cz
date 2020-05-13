---
title: ICorDebugStepperEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
ms.openlocfilehash: c39c047cce97db7c98f1fad403bd16d0e6a2c0fe
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379445"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="4740a-102">ICorDebugStepperEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4740a-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="4740a-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="4740a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4740a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4740a-104">Methods</span></span>  
  
|<span data-ttu-id="4740a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4740a-105">Method</span></span>|<span data-ttu-id="4740a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4740a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4740a-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4740a-107">Next Method</span></span>](icordebugstepperenum-next-method.md)|<span data-ttu-id="4740a-108">Získá zadaný počet `ICorDebugStepper` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="4740a-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4740a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4740a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4740a-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4740a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4740a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4740a-111">Requirements</span></span>  
 <span data-ttu-id="4740a-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4740a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4740a-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4740a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4740a-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4740a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4740a-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4740a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4740a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4740a-116">See also</span></span>

- [<span data-ttu-id="4740a-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4740a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
