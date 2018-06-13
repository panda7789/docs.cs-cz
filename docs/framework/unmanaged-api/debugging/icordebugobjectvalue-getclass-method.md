---
title: ICorDebugObjectValue::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dff7a42cac7002e170e8da3c3505fe37bd5eb85f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418760"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="14f99-102">ICorDebugObjectValue::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="14f99-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="14f99-103">Získá třídu hodnota tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="14f99-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14f99-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14f99-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14f99-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="14f99-106">[out] Ukazatel na adresu "ICorDebugClass" objekt, který představuje třídu objektu hodnoty, představuje tento objekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="14f99-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14f99-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14f99-107">Remarks</span></span>  
 <span data-ttu-id="14f99-108">`GetClass` a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) každá z metod vrácení informací o typu hodnoty; obě jsou nahrazeny touto obecné typy podporující [icordebugvalue2::getexacttype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="14f99-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14f99-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14f99-109">Requirements</span></span>  
 <span data-ttu-id="14f99-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f99-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f99-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14f99-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14f99-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14f99-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14f99-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f99-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f99-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14f99-114">See Also</span></span>  
    
 
