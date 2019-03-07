---
title: ICorDebugProcess5::GetArrayLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5cff3f3f577a0c7ef04a226ec70a2722c89b5c8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496882"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="8a06f-102">ICorDebugProcess5::GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="8a06f-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="8a06f-103">Poskytuje informace o rozložení typy polí.</span><span class="sxs-lookup"><span data-stu-id="8a06f-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a06f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a06f-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a06f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a06f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="8a06f-106">[in] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje pole, jehož rozložení je žádoucí.</span><span class="sxs-lookup"><span data-stu-id="8a06f-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="8a06f-107">[out] Ukazatel [cor_array_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) strukturu, která obsahuje informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="8a06f-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a06f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a06f-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a06f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8a06f-109">Requirements</span></span>  
 <span data-ttu-id="8a06f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a06f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a06f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a06f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a06f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a06f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a06f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a06f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a06f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a06f-114">See also</span></span>
- [<span data-ttu-id="8a06f-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8a06f-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="8a06f-116">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8a06f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
