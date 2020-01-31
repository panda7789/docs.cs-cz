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
ms.openlocfilehash: d154cf10e60935d12653c70875323079f92ae288
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791734"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="59ac8-102">ICorDebugStepper2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="59ac8-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="59ac8-103">Poskytuje podporu pro ladění pouze můj kód (JMC).</span><span class="sxs-lookup"><span data-stu-id="59ac8-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59ac8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59ac8-104">Methods</span></span>  
  
|<span data-ttu-id="59ac8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59ac8-105">Method</span></span>|<span data-ttu-id="59ac8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="59ac8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59ac8-107">SetJMC – metoda</span><span class="sxs-lookup"><span data-stu-id="59ac8-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="59ac8-108">Nastaví hodnotu, která určuje, zda jsou tyto ICorDebugStepper kroky pouze prostřednictvím kódu, který je vytvořen vývojářem aplikace.</span><span class="sxs-lookup"><span data-stu-id="59ac8-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ac8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59ac8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59ac8-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="59ac8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59ac8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59ac8-111">Requirements</span></span>  
 <span data-ttu-id="59ac8-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59ac8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59ac8-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="59ac8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59ac8-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="59ac8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59ac8-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59ac8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ac8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59ac8-116">See also</span></span>

- [<span data-ttu-id="59ac8-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="59ac8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
