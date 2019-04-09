---
title: ICorDebugObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0144539987f14bed83bfc9eab2f5ca26d2a609ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157729"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="b3cf5-102">ICorDebugObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3cf5-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="b3cf5-103">Implementuje metody ICorDebugEnum a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="b3cf5-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3cf5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b3cf5-104">Methods</span></span>  
  
|<span data-ttu-id="b3cf5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3cf5-105">Method</span></span>|<span data-ttu-id="b3cf5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b3cf5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3cf5-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b3cf5-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="b3cf5-108">Získá RVA zadané počty objektů z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="b3cf5-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3cf5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3cf5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3cf5-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b3cf5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3cf5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3cf5-111">Requirements</span></span>  
 <span data-ttu-id="b3cf5-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3cf5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3cf5-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3cf5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3cf5-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3cf5-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b3cf5-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b3cf5-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3cf5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3cf5-116">See also</span></span>

- [<span data-ttu-id="b3cf5-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b3cf5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
