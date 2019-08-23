---
title: ICorDebugStringValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cfaf886d09d843f4dbf61af55a9388454b050ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957430"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="20975-102">ICorDebugStringValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20975-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="20975-103">Podtřída ICorDebugHeapValue, která se vztahuje na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="20975-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20975-104">Metody</span><span class="sxs-lookup"><span data-stu-id="20975-104">Methods</span></span>  
  
|<span data-ttu-id="20975-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="20975-105">Method</span></span>|<span data-ttu-id="20975-106">Popis</span><span class="sxs-lookup"><span data-stu-id="20975-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20975-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="20975-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="20975-108">Vrátí počet znaků v řetězci, na který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="20975-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="20975-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="20975-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="20975-110">Získá řetězec, na který odkazuje `ICorDebugStringValue`tento.</span><span class="sxs-lookup"><span data-stu-id="20975-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20975-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20975-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20975-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="20975-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20975-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20975-113">Requirements</span></span>  
 <span data-ttu-id="20975-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20975-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20975-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="20975-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20975-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20975-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20975-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20975-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20975-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20975-118">See also</span></span>

- [<span data-ttu-id="20975-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="20975-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
