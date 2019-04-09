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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093745"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="6bb9e-102">ICorDebugVariableHome::GetSlotIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="6bb9e-102">ICorDebugVariableHome::GetSlotIndex Method</span></span>
<span data-ttu-id="6bb9e-103">Získá spravované slotu index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-103">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb9e-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bb9e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bb9e-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="6bb9e-106">[out] Ukazatel pozice index lokální proměnné.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-106">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bb9e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6bb9e-107">Return Value</span></span>  
 <span data-ttu-id="6bb9e-108">Metoda vrátí následující hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="6bb9e-109">Value</span><span class="sxs-lookup"><span data-stu-id="6bb9e-109">Value</span></span>|<span data-ttu-id="6bb9e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6bb9e-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="6bb9e-111">Volání metody, které vrátil hodnotu index pozice v `pSlotIndex`.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-111">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="6bb9e-112">Aktuální [icordebugvariablehome –](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) představuje instanci jako argument funkce.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb9e-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6bb9e-113">Remarks</span></span>  
 <span data-ttu-id="6bb9e-114">Index pozice, je možné načíst metadata pro tuto místní proměnnou.</span><span class="sxs-lookup"><span data-stu-id="6bb9e-114">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb9e-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bb9e-115">Requirements</span></span>  
 <span data-ttu-id="6bb9e-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb9e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb9e-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6bb9e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bb9e-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6bb9e-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6bb9e-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6bb9e-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6bb9e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bb9e-120">See also</span></span>

- [<span data-ttu-id="6bb9e-121">ICorDebugVariableHome – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bb9e-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
