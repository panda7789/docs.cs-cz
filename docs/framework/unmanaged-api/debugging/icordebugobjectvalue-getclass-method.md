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
ms.openlocfilehash: 4719f155957f04471d4ad2b8d71bec9c0f0d30c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096090"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="7edfe-102">ICorDebugObjectValue::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="7edfe-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="7edfe-103">Získá třídu této hodnoty objektu.</span><span class="sxs-lookup"><span data-stu-id="7edfe-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7edfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7edfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7edfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7edfe-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="7edfe-106">mimo Ukazatel na adresu objektu "ICorDebugClass", který představuje třídu hodnoty objektu reprezentované tímto objektem "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="7edfe-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7edfe-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7edfe-107">Remarks</span></span>  
 <span data-ttu-id="7edfe-108">Metody `GetClass` a [ICorDebugValue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) vrátí informace o typu hodnoty; jsou obě nahrazeny obecnými [ICorDebugValue2:: GetExactType –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="7edfe-108">The `GetClass` and [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7edfe-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7edfe-109">Requirements</span></span>  
 <span data-ttu-id="7edfe-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7edfe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7edfe-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7edfe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7edfe-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7edfe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7edfe-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7edfe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edfe-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7edfe-114">See also</span></span>
