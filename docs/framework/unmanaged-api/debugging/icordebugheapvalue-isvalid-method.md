---
title: ICorDebugHeapValue::IsValid – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ca3b86e90dcb76c1fece44cf2c5ed68e073d8e7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757217"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="42871-102">ICorDebugHeapValue::IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="42871-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="42871-103">Získá hodnotu určující, zda objekt reprezentovaný rozhraním tento ICorDebugHeapValue je platný.</span><span class="sxs-lookup"><span data-stu-id="42871-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="42871-104">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="42871-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42871-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42871-105">Syntax</span></span>  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42871-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="42871-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="42871-107">[out] Ukazatel na logickou hodnotu určující, zda je platný tuto hodnotu na haldě.</span><span class="sxs-lookup"><span data-stu-id="42871-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42871-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42871-108">Remarks</span></span>  
 <span data-ttu-id="42871-109">Hodnota není platná, pokud byl uvolněn systémem uvolňování.</span><span class="sxs-lookup"><span data-stu-id="42871-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="42871-110">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="42871-110">This method has been deprecated.</span></span> <span data-ttu-id="42871-111">V rozhraní .NET Framework 2.0, jsou všechny hodnoty platné až do [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volán, na kterém jsou neplatné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="42871-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42871-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42871-112">Requirements</span></span>  
 <span data-ttu-id="42871-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42871-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42871-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42871-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42871-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42871-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42871-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42871-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
