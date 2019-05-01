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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26efb3e43642b6d1fd10b084c2b321609c89d89b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994679"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="fdcca-102">ICorDebugModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdcca-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="fdcca-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="fdcca-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdcca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fdcca-104">Methods</span></span>  
  
|<span data-ttu-id="fdcca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fdcca-105">Method</span></span>|<span data-ttu-id="fdcca-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fdcca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdcca-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="fdcca-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="fdcca-108">Získá zadaný počet `ICorDebugModule` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="fdcca-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdcca-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdcca-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdcca-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="fdcca-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdcca-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdcca-111">Requirements</span></span>  
 <span data-ttu-id="fdcca-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdcca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdcca-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdcca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdcca-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdcca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdcca-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdcca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdcca-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdcca-116">See also</span></span>

- [<span data-ttu-id="fdcca-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fdcca-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
