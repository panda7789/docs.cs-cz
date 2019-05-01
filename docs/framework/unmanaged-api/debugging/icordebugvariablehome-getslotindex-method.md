---
title: ICorDebugVariableHome::GetSlotIndex – metoda
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b819f1f02870a8a85a531d7d341cbaf488a1ccd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993665"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="5611b-102">ICorDebugVariableHome::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="5611b-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="5611b-103">Získá spravované slotu index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="5611b-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5611b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5611b-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5611b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5611b-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="5611b-106">[out] Ukazatel pozice index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="5611b-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5611b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5611b-107">Return Value</span></span>  
 <span data-ttu-id="5611b-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5611b-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="5611b-109">Value</span><span class="sxs-lookup"><span data-stu-id="5611b-109">Value</span></span>|<span data-ttu-id="5611b-110">Popis</span><span class="sxs-lookup"><span data-stu-id="5611b-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5611b-111">Volání metody, které vrátil hodnotu index pozice v `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="5611b-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5611b-112">Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) představuje instanci jako argument funkce.</span><span class="sxs-lookup"><span data-stu-id="5611b-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5611b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5611b-113">Remarks</span></span>  
 <span data-ttu-id="5611b-114">Index pozice, je možné načíst metadata pro tuto místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="5611b-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5611b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5611b-115">Requirements</span></span>  
 <span data-ttu-id="5611b-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5611b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5611b-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5611b-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5611b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5611b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5611b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5611b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5611b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5611b-120">See also</span></span>

- [<span data-ttu-id="5611b-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5611b-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
