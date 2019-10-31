---
title: ICorDebugValue3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 1f46866a1b975455acd294221e38ef3b4c358660
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140203"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="5a5b7-102">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5a5b7-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="5a5b7-103">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" tak, aby poskytovala podporu pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a5b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5a5b7-104">Methods</span></span>  
  
|<span data-ttu-id="5a5b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5a5b7-105">Method</span></span>|<span data-ttu-id="5a5b7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5a5b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a5b7-107">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="5a5b7-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="5a5b7-108">Získá velikost objektu `ICorDebugValue3` v bajtech.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a5b7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a5b7-109">Remarks</span></span>  
 <span data-ttu-id="5a5b7-110">Metoda [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) vrátí velikost objektu, který je v rozsahu od 0 do 2 147 483 647 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="5a5b7-111">V .NET Framework 4,5 může velikost polí překročit 2 GB.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="5a5b7-112">Rozhraní `ICorDebugValue3` umožňuje určit velikost těchto polí.</span><span class="sxs-lookup"><span data-stu-id="5a5b7-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a5b7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5a5b7-113">Requirements</span></span>  
 <span data-ttu-id="5a5b7-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a5b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a5b7-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a5b7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a5b7-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5a5b7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a5b7-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a5b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5b7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a5b7-118">See also</span></span>

- [<span data-ttu-id="5a5b7-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5a5b7-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5a5b7-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="5a5b7-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
