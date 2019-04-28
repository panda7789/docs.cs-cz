---
title: ICorDebugAssemblyEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fef4d757cf528cd3dc7d79db04d33c2cad9bbf1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645497"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="a1236-102">ICorDebugAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1236-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="a1236-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="a1236-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1236-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1236-104">Methods</span></span>  
  
|<span data-ttu-id="a1236-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1236-105">Method</span></span>|<span data-ttu-id="a1236-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a1236-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1236-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a1236-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="a1236-108">Získá zadaný počet `ICorDebugAssembly` instancí ve výčtu, od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="a1236-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1236-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1236-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1236-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a1236-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1236-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1236-111">Requirements</span></span>  
 <span data-ttu-id="a1236-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1236-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1236-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1236-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1236-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1236-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1236-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1236-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1236-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1236-116">See also</span></span>

- [<span data-ttu-id="a1236-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a1236-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
