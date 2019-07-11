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
ms.openlocfilehash: 7a20ab7a7ecb5d01351d0c912e08955f44b26d5f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756995"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="a6f7e-102">ICorDebugObjectValue::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="a6f7e-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="a6f7e-103">Získá třídu hodnota tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="a6f7e-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6f7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f7e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6f7e-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="a6f7e-106">[out] Ukazatel na adresu "ICorDebugClass" objekt, který představuje třídu hodnota objekt reprezentovaný tímto objektem "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="a6f7e-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6f7e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6f7e-107">Remarks</span></span>  
 <span data-ttu-id="a6f7e-108">`GetClass` a [icordebugvalue::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) každá z metod vrací informace o typu hodnoty; jsou obě nahrazeny obecných typů podporujících [icordebugvalue2::getexacttype –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6f7e-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f7e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6f7e-109">Requirements</span></span>  
 <span data-ttu-id="a6f7e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f7e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f7e-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6f7e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6f7e-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6f7e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6f7e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f7e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f7e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6f7e-114">See also</span></span>
