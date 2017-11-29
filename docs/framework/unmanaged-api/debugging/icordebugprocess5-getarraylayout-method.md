---
title: "ICorDebugProcess5::GetArrayLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetArrayLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4c5d07e1645bc3736de2f8a298ad5b80e2cb26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="c232d-102">ICorDebugProcess5::GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="c232d-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="c232d-103">Poskytuje informace o rozložení typy polí.</span><span class="sxs-lookup"><span data-stu-id="c232d-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c232d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c232d-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c232d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c232d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="c232d-106">[v] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje pole, jejichž uspořádání se požaduje.</span><span class="sxs-lookup"><span data-stu-id="c232d-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="c232d-107">[out] Ukazatel [cor_array_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) struktura, která obsahuje informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="c232d-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c232d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c232d-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c232d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c232d-109">Requirements</span></span>  
 <span data-ttu-id="c232d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c232d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c232d-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c232d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c232d-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c232d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c232d-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c232d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c232d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c232d-114">See Also</span></span>  
 [<span data-ttu-id="c232d-115">ICorDebugProcess5 – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="c232d-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="c232d-116">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="c232d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
