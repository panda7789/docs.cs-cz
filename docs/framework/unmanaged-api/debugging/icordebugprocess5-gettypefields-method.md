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
ms.openlocfilehash: 644b5ed751caaf1809250244b37badc8037b0f57
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792345"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="7b251-102">ICorDebugProcess5::GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="7b251-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="7b251-103">Poskytuje informace o polích, která patří do typu.</span><span class="sxs-lookup"><span data-stu-id="7b251-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b251-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b251-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b251-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7b251-106">pro Identifikátor typu, jehož informace o poli jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="7b251-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="7b251-107">pro Počet objektů [COR_FIELD](cor-field-structure.md) , jejichž informace o poli mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="7b251-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="7b251-108">mimo Pole objektů [COR_FIELD](cor-field-structure.md) , které poskytují informace o polích, která patří do typu.</span><span class="sxs-lookup"><span data-stu-id="7b251-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="7b251-109">mimo Ukazatel na počet objektů [COR_FIELD](cor-field-structure.md) obsažených v `fields`.</span><span class="sxs-lookup"><span data-stu-id="7b251-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b251-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b251-110">Remarks</span></span>  
 <span data-ttu-id="7b251-111">Parametr `celt`, který určuje počet polí, jejichž informace o poli, kterou metoda používá k naplnění `fields`, by měla odpovídat hodnotě pole `COR_TYPE_LAYOUT::numFields`.</span><span class="sxs-lookup"><span data-stu-id="7b251-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b251-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b251-112">Requirements</span></span>  
 <span data-ttu-id="7b251-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b251-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b251-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b251-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b251-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b251-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b251-116">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b251-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b251-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b251-117">See also</span></span>

- [<span data-ttu-id="7b251-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b251-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="7b251-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7b251-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
