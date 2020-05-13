---
title: ICorDebugModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: ccb9eff963da1d502d1ed789640f1a108676754c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213345"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="fa960-102">ICorDebugModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa960-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="fa960-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="fa960-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa960-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fa960-104">Methods</span></span>  
  
|<span data-ttu-id="fa960-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa960-105">Method</span></span>|<span data-ttu-id="fa960-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fa960-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa960-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="fa960-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="fa960-108">Získá zadaný počet `ICorDebugModule` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="fa960-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa960-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa960-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa960-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fa960-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa960-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa960-111">Requirements</span></span>  
 <span data-ttu-id="fa960-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa960-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa960-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fa960-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa960-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fa960-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa960-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa960-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa960-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa960-116">See also</span></span>

- [<span data-ttu-id="fa960-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fa960-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
