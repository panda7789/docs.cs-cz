---
title: ICorDebugCodeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: cce0efa925683b5361a5422112db3f8231e2dfb4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893280"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="0dc00-102">ICorDebugCodeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0dc00-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="0dc00-103">Implementuje metody "ICorDebugEnum" a vytvoří výčet polí "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="0dc00-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0dc00-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0dc00-104">Methods</span></span>  
  
|<span data-ttu-id="0dc00-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0dc00-105">Method</span></span>|<span data-ttu-id="0dc00-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0dc00-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0dc00-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0dc00-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="0dc00-108">Získá zadaný počet `ICorDebugCode` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="0dc00-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dc00-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0dc00-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0dc00-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0dc00-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc00-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0dc00-111">Requirements</span></span>  
 <span data-ttu-id="0dc00-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dc00-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dc00-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0dc00-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dc00-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0dc00-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dc00-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dc00-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc00-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0dc00-116">See also</span></span>

- [<span data-ttu-id="0dc00-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0dc00-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
