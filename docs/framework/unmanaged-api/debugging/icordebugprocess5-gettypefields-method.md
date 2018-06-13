---
title: ICorDebugProcess5::GetTypeFields – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214fc97e41d8d220547a5f8bd28117ff411fa89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418402"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="db7c6-102">ICorDebugProcess5::GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="db7c6-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="db7c6-103">Poskytuje informace o pole, které patří do typu.</span><span class="sxs-lookup"><span data-stu-id="db7c6-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db7c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db7c6-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db7c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db7c6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="db7c6-106">[v] Identifikátor typu je načíst informace o jejichž pole.</span><span class="sxs-lookup"><span data-stu-id="db7c6-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="db7c6-107">[v] Počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, jejichž informace pole se mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="db7c6-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="db7c6-108">[out] Pole [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, které obsahují informace o pole, které patří k typu.</span><span class="sxs-lookup"><span data-stu-id="db7c6-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="db7c6-109">[out] Ukazatel na počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objektů obsažených v `fields`.</span><span class="sxs-lookup"><span data-stu-id="db7c6-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db7c6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db7c6-110">Remarks</span></span>  
 <span data-ttu-id="db7c6-111">`celt` Parametr, který určuje počet polí, jejichž pole informace metoda používá k naplnění `fields`, by měla odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.</span><span class="sxs-lookup"><span data-stu-id="db7c6-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db7c6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db7c6-112">Requirements</span></span>  
 <span data-ttu-id="db7c6-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db7c6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db7c6-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db7c6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db7c6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db7c6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db7c6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db7c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7c6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="db7c6-117">See Also</span></span>  
 [<span data-ttu-id="db7c6-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db7c6-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="db7c6-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="db7c6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
