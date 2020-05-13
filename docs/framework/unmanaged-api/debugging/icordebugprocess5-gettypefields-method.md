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
ms.openlocfilehash: a2c7f7b722abac6acf71d3b64276862441695a5f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212786"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="41e99-102">ICorDebugProcess5::GetTypeFields – metoda</span><span class="sxs-lookup"><span data-stu-id="41e99-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="41e99-103">Poskytuje informace o polích, která patří do typu.</span><span class="sxs-lookup"><span data-stu-id="41e99-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e99-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41e99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41e99-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="41e99-106">pro Identifikátor typu, jehož informace o poli jsou načteny.</span><span class="sxs-lookup"><span data-stu-id="41e99-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="41e99-107">pro Počet objektů [COR_FIELD](cor-field-structure.md) , jejichž informace o poli mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="41e99-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="41e99-108">mimo Pole objektů [COR_FIELD](cor-field-structure.md) , které poskytují informace o polích, která patří do typu.</span><span class="sxs-lookup"><span data-stu-id="41e99-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="41e99-109">mimo Ukazatel na počet objektů [COR_FIELD](cor-field-structure.md) obsažených v `fields` .</span><span class="sxs-lookup"><span data-stu-id="41e99-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41e99-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41e99-110">Remarks</span></span>  
 <span data-ttu-id="41e99-111">`celt`Parametr, který určuje počet polí, jejichž informace o poli, kterou metoda používá k naplnění `fields` , by měla odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.</span><span class="sxs-lookup"><span data-stu-id="41e99-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e99-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41e99-112">Requirements</span></span>  
 <span data-ttu-id="41e99-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e99-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e99-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41e99-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41e99-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41e99-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e99-116">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e99-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="41e99-117">See also</span></span>

- [<span data-ttu-id="41e99-118">ICorDebugProcess5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41e99-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="41e99-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41e99-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
