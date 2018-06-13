---
title: ICorDebugObjectEnum Interface1
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
ms.openlocfilehash: 3674643d5590c320bddd5a0e6f1f95814e07ecf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420200"
---
# <a name="icordebugobjectenum-interface1"></a><span data-ttu-id="8870d-102">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="8870d-102">ICorDebugObjectEnum Interface1</span></span>
<span data-ttu-id="8870d-103">Implementuje metody ICorDebugEnum a zobrazí pole objektů podle jejich relativní virtuální adresy (RVAs).</span><span class="sxs-lookup"><span data-stu-id="8870d-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8870d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8870d-104">Methods</span></span>  
  
|<span data-ttu-id="8870d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8870d-105">Method</span></span>|<span data-ttu-id="8870d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8870d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8870d-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="8870d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="8870d-108">Získá RVAs o zadaný počet objektů z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="8870d-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8870d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8870d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8870d-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8870d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8870d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8870d-111">Requirements</span></span>  
 <span data-ttu-id="8870d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8870d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8870d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8870d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8870d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8870d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8870d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8870d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8870d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8870d-116">See Also</span></span>  
 [<span data-ttu-id="8870d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8870d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
