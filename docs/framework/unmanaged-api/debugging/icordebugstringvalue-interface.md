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
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138947"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="db77c-102">ICorDebugStringValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db77c-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="db77c-103">Podtřída ICorDebugHeapValue, která se vztahuje na řetězcové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db77c-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="db77c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="db77c-104">Methods</span></span>  
  
|<span data-ttu-id="db77c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="db77c-105">Method</span></span>|<span data-ttu-id="db77c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="db77c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="db77c-107">GetLength – metoda</span><span class="sxs-lookup"><span data-stu-id="db77c-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="db77c-108">Vrátí počet znaků v řetězci, na který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="db77c-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="db77c-109">GetString – metoda</span><span class="sxs-lookup"><span data-stu-id="db77c-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="db77c-110">Získá řetězec, na který odkazuje tento `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="db77c-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db77c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db77c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db77c-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="db77c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db77c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db77c-113">Requirements</span></span>  
 <span data-ttu-id="db77c-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db77c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db77c-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db77c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db77c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="db77c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db77c-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db77c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db77c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db77c-118">See also</span></span>

- [<span data-ttu-id="db77c-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db77c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
