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
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948717"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="da17b-102">ICorDebugProcess5::GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="da17b-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="da17b-103">Poskytuje informace o polích, které patří k typu.</span><span class="sxs-lookup"><span data-stu-id="da17b-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da17b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da17b-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da17b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da17b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="da17b-106">[in] Identifikátor typu, jehož informace v poli je načten.</span><span class="sxs-lookup"><span data-stu-id="da17b-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="da17b-107">[in] Počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, jejichž informace z pole má být načtena.</span><span class="sxs-lookup"><span data-stu-id="da17b-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="da17b-108">[out] Pole [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, které poskytují informace o polích, které patří do typu.</span><span class="sxs-lookup"><span data-stu-id="da17b-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="da17b-109">[out] Ukazatel na počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objektů obsažených v `fields`.</span><span class="sxs-lookup"><span data-stu-id="da17b-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da17b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da17b-110">Remarks</span></span>  
 <span data-ttu-id="da17b-111">`celt` Parametr, který určuje počet polí, jejichž informace v poli Metoda používá k naplnění `fields`, by měl odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.</span><span class="sxs-lookup"><span data-stu-id="da17b-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da17b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da17b-112">Requirements</span></span>  
 <span data-ttu-id="da17b-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da17b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da17b-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da17b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da17b-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da17b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da17b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da17b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da17b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da17b-117">See also</span></span>

- [<span data-ttu-id="da17b-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da17b-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="da17b-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="da17b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
