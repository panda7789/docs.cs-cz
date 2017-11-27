---
title: ICorDebugObjectEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectEnum
helpviewer_keywords: ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: baa8ea056c457455482a5f7631956f7edce0ac91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="7fca7-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="7fca7-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="7fca7-103">Implementuje metody ICorDebugEnum a zobrazí pole objektů podle jejich relativní virtuální adresy (RVAs).</span><span class="sxs-lookup"><span data-stu-id="7fca7-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fca7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7fca7-104">Methods</span></span>  
  
|<span data-ttu-id="7fca7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fca7-105">Method</span></span>|<span data-ttu-id="7fca7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7fca7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fca7-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7fca7-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="7fca7-108">Získá RVAs o zadaný počet objektů z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="7fca7-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fca7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fca7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fca7-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7fca7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fca7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fca7-111">Requirements</span></span>  
 <span data-ttu-id="7fca7-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fca7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fca7-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fca7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fca7-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fca7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fca7-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fca7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fca7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fca7-116">See Also</span></span>  
 [<span data-ttu-id="7fca7-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7fca7-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
