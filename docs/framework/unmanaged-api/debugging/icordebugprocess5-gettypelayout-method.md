---
title: ICorDebugProcess5::GetTypeLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16da3948d89febc12a72ef54fbc060689a3964c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423244"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="a583d-102">ICorDebugProcess5::GetTypeLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="a583d-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="a583d-103">Získá informace o rozložení objektu v paměti podle jeho typ identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a583d-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a583d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a583d-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a583d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a583d-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a583d-106">[v] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje typ, jejichž uspořádání se požaduje.</span><span class="sxs-lookup"><span data-stu-id="a583d-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="a583d-107">[out] Ukazatel [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktura, která obsahuje informace o rozložení objektu v paměti.</span><span class="sxs-lookup"><span data-stu-id="a583d-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a583d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a583d-108">Remarks</span></span>  
 <span data-ttu-id="a583d-109">`ICorDebugProcess5::GetTypeLayout` Metoda poskytuje informace o objekt na základě jeho [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která vrátí počet dalších [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a583d-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="a583d-110">Poskytuje informace [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktura, který je vyplněný metodou.</span><span class="sxs-lookup"><span data-stu-id="a583d-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a583d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a583d-111">Requirements</span></span>  
 <span data-ttu-id="a583d-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a583d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a583d-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a583d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a583d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a583d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a583d-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a583d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a583d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a583d-116">See Also</span></span>  
 [<span data-ttu-id="a583d-117">COR_TYPE_LAYOUT – struktura</span><span class="sxs-lookup"><span data-stu-id="a583d-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="a583d-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a583d-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="a583d-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a583d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
