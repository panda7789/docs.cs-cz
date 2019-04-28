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
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700226"
---
# <a name="icordebugheapvalueisvalid-method"></a><span data-ttu-id="24bc0-102">ICorDebugHeapValue::IsValid – metoda</span><span class="sxs-lookup"><span data-stu-id="24bc0-102">ICorDebugHeapValue::IsValid Method</span></span>
<span data-ttu-id="24bc0-103">Získá hodnotu určující, zda objekt reprezentovaný rozhraním tento ICorDebugHeapValue je platný.</span><span class="sxs-lookup"><span data-stu-id="24bc0-103">Gets a value that indicates whether the object represented by this ICorDebugHeapValue is valid.</span></span>  
  
 <span data-ttu-id="24bc0-104">Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="24bc0-104">This method has been deprecated in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24bc0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24bc0-105">Syntax</span></span>  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24bc0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="24bc0-106">Parameters</span></span>  
 `pbValid`  
 <span data-ttu-id="24bc0-107">[out] Ukazatel na logickou hodnotu určující, zda je platný tuto hodnotu na haldě.</span><span class="sxs-lookup"><span data-stu-id="24bc0-107">[out] A pointer to a Boolean value that indicates whether this value on the heap is valid.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24bc0-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24bc0-108">Remarks</span></span>  
 <span data-ttu-id="24bc0-109">Hodnota není platná, pokud byl uvolněn systémem uvolňování.</span><span class="sxs-lookup"><span data-stu-id="24bc0-109">The value is invalid if it has been reclaimed by the garbage collector.</span></span>  
  
 <span data-ttu-id="24bc0-110">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="24bc0-110">This method has been deprecated.</span></span> <span data-ttu-id="24bc0-111">V rozhraní .NET Framework 2.0, jsou všechny hodnoty platné až do [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volán, na kterém jsou neplatné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="24bc0-111">In the .NET Framework 2.0, all values are valid until [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called, at which time the values are invalidated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24bc0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24bc0-112">Requirements</span></span>  
 <span data-ttu-id="24bc0-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24bc0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24bc0-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24bc0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24bc0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24bc0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24bc0-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24bc0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
