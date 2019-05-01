---
title: ICorDebugStepper2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987412"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="ff2aa-102">ICorDebugStepper2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ff2aa-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="ff2aa-103">Poskytuje podporu pro pouze můj kód (JMC) ladění.</span><span class="sxs-lookup"><span data-stu-id="ff2aa-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff2aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ff2aa-104">Methods</span></span>  
  
|<span data-ttu-id="ff2aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ff2aa-105">Method</span></span>|<span data-ttu-id="ff2aa-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ff2aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff2aa-107">SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="ff2aa-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="ff2aa-108">Nastaví hodnotu, která určuje, zda tento icordebugstepper – provede pouze kód, který je vytvořený vývojářem aplikace.</span><span class="sxs-lookup"><span data-stu-id="ff2aa-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff2aa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff2aa-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff2aa-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="ff2aa-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2aa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ff2aa-111">Requirements</span></span>  
 <span data-ttu-id="ff2aa-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff2aa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2aa-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff2aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff2aa-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2aa-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2aa-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff2aa-116">See also</span></span>

- [<span data-ttu-id="ff2aa-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ff2aa-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
