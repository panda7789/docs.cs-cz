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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221974"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="0689e-102">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0689e-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="0689e-103">Rozšiřuje rozhraní "ICorDebugValue" a "ICorDebugValue2" k poskytování podpory pro pole, která jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="0689e-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0689e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0689e-104">Methods</span></span>  
  
|<span data-ttu-id="0689e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0689e-105">Method</span></span>|<span data-ttu-id="0689e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0689e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0689e-107">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="0689e-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="0689e-108">Získá velikost v bajtech, to `ICorDebugValue3` objektu.</span><span class="sxs-lookup"><span data-stu-id="0689e-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0689e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0689e-109">Remarks</span></span>  
 <span data-ttu-id="0689e-110">[Icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda vrátí objekt velikost, rozsahu od 0 do 2 147 483 647 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0689e-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="0689e-111">V [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], velikost pole může být delší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="0689e-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="0689e-112">`ICorDebugValue3` Rozhraní vám umožní určit velikost těchto polí.</span><span class="sxs-lookup"><span data-stu-id="0689e-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0689e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0689e-113">Requirements</span></span>  
 <span data-ttu-id="0689e-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0689e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0689e-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0689e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0689e-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0689e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0689e-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0689e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0689e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0689e-118">See also</span></span>

- [<span data-ttu-id="0689e-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0689e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0689e-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="0689e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
