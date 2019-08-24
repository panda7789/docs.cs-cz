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
ms.openlocfilehash: 6c557df3c69b9d18b95ebf33815b92dcb9097f4e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69987539"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="30638-102">ICorDebugAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="30638-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="30638-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="30638-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30638-104">Metody</span><span class="sxs-lookup"><span data-stu-id="30638-104">Methods</span></span>  
  
|<span data-ttu-id="30638-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="30638-105">Method</span></span>|<span data-ttu-id="30638-106">Popis</span><span class="sxs-lookup"><span data-stu-id="30638-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30638-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="30638-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="30638-108">Získá zadaný počet `ICorDebugAssembly` instancí ve výčtu, počínaje od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="30638-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30638-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30638-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30638-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="30638-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30638-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30638-111">Requirements</span></span>  
 <span data-ttu-id="30638-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30638-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30638-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="30638-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30638-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30638-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30638-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30638-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30638-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30638-116">See also</span></span>

- [<span data-ttu-id="30638-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="30638-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
