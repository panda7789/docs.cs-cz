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
ms.openlocfilehash: 332de11790e78b712a429365bd89cc9e41539edc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105518"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="64067-102">ICorDebugProcess5::GetArrayLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="64067-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="64067-103">Poskytuje informace o rozložení typy polí.</span><span class="sxs-lookup"><span data-stu-id="64067-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64067-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64067-104">Syntax</span></span>  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64067-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64067-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="64067-106">[in] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje pole, jehož rozložení je žádoucí.</span><span class="sxs-lookup"><span data-stu-id="64067-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="64067-107">[out] Ukazatel [cor_array_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) strukturu, která obsahuje informace o rozložení pole v paměti.</span><span class="sxs-lookup"><span data-stu-id="64067-107">[out] A pointer to a [COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64067-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64067-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64067-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64067-109">Requirements</span></span>  
 <span data-ttu-id="64067-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64067-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64067-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64067-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64067-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64067-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="64067-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="64067-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64067-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64067-114">See also</span></span>

- [<span data-ttu-id="64067-115">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-115">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="64067-116">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64067-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
