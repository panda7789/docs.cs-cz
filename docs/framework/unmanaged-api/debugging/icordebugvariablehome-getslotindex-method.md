---
title: 'ICorDebugVariableHome:: GetSlotIndex – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 0bffd2db0a4a061a8629ff50a03a319feec6d836
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396554"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="d7cbd-102">ICorDebugVariableHome:: GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="d7cbd-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="d7cbd-103">Získá spravovaný index slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7cbd-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7cbd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7cbd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7cbd-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d7cbd-106">mimo Ukazatel na index slotu místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="d7cbd-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7cbd-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d7cbd-107">Return Value</span></span>  
 <span data-ttu-id="d7cbd-108">Metoda vrací následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d7cbd-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d7cbd-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d7cbd-109">Value</span></span>|<span data-ttu-id="d7cbd-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d7cbd-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="d7cbd-111">Volání metody vrátilo hodnotu indexu slotu v `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="d7cbd-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="d7cbd-112">Aktuální instance [ICorDebugVariableHome](icordebugvariablehome-interface.md) představuje argument funkce.</span><span class="sxs-lookup"><span data-stu-id="d7cbd-112">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7cbd-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7cbd-113">Remarks</span></span>  
 <span data-ttu-id="d7cbd-114">Index slotu lze použít k načtení metadat pro tuto místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d7cbd-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7cbd-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7cbd-115">Requirements</span></span>  
 <span data-ttu-id="d7cbd-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7cbd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7cbd-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7cbd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7cbd-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d7cbd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7cbd-119">**Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7cbd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7cbd-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7cbd-120">See also</span></span>

- [<span data-ttu-id="d7cbd-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7cbd-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
