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
ms.openlocfilehash: 6bc24450cdda2e3ed324256b53b2d137d1eb90e4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788489"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="52567-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52567-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="52567-103">Představuje interní rámec modulu runtime v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="52567-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="52567-104">Toto rozhraní je podtřídou rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="52567-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52567-105">Metody</span><span class="sxs-lookup"><span data-stu-id="52567-105">Methods</span></span>  
  
|<span data-ttu-id="52567-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="52567-106">Method</span></span>|<span data-ttu-id="52567-107">Popis</span><span class="sxs-lookup"><span data-stu-id="52567-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52567-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="52567-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="52567-109">Získá typ tohoto interního rámce.</span><span class="sxs-lookup"><span data-stu-id="52567-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52567-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52567-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52567-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="52567-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52567-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52567-112">Requirements</span></span>  
 <span data-ttu-id="52567-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52567-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52567-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="52567-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52567-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="52567-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52567-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52567-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52567-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52567-117">See also</span></span>

- [<span data-ttu-id="52567-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="52567-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
