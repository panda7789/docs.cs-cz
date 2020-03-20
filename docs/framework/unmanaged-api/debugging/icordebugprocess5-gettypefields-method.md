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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178594"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="687ee-102">ICorDebugProcess5::GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="687ee-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="687ee-103">Obsahuje informace o polích, která patří k typu.</span><span class="sxs-lookup"><span data-stu-id="687ee-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="687ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="687ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="687ee-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="687ee-106">[v] Identifikátor typu, jehož informace o poli jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="687ee-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="687ee-107">[v] Počet [COR_FIELD](cor-field-structure.md) objektů, jejichž informace o poli má být načten.</span><span class="sxs-lookup"><span data-stu-id="687ee-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="687ee-108">[out] Pole [COR_FIELD](cor-field-structure.md) objekty, které poskytují informace o polích, které patří k typu.</span><span class="sxs-lookup"><span data-stu-id="687ee-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="687ee-109">[out] Ukazatel na počet [COR_FIELD](cor-field-structure.md) objektů `fields`zahrnutých v .</span><span class="sxs-lookup"><span data-stu-id="687ee-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="687ee-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="687ee-110">Remarks</span></span>  
 <span data-ttu-id="687ee-111">Parametr, `celt` který určuje počet polí, jejichž informace o `fields`polích, které metoda `COR_TYPE_LAYOUT::numFields` používá k naplnění , by měl odpovídat hodnotě pole.</span><span class="sxs-lookup"><span data-stu-id="687ee-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="687ee-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="687ee-112">Requirements</span></span>  
 <span data-ttu-id="687ee-113">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="687ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="687ee-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="687ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="687ee-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="687ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="687ee-116">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="687ee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687ee-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="687ee-117">See also</span></span>

- [<span data-ttu-id="687ee-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="687ee-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="687ee-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="687ee-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
