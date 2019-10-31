---
title: ICorDebugValue2::GetExactType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: 441d225dadbbca09ab27c8ccd70debe32f4c12da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140264"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="9181c-102">ICorDebugValue2::GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="9181c-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="9181c-103">Získá ukazatel rozhraní na objekt "ICorDebugType", který představuje <xref:System.Type> této hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9181c-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9181c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9181c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9181c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9181c-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="9181c-106">mimo Ukazatel na adresu `ICorDebugType`ho objektu, který představuje <xref:System.Type> hodnoty reprezentované tímto objektem "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="9181c-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9181c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9181c-107">Remarks</span></span>  
 <span data-ttu-id="9181c-108">Metoda `GetExactType` s obecnými typy nahrazuje obě metody [ICorDebugObjectValue:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) a [ICorDebugValue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) , z nichž každý vrací informace o typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9181c-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9181c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9181c-109">Requirements</span></span>  
 <span data-ttu-id="9181c-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9181c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9181c-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9181c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9181c-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9181c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9181c-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9181c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9181c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9181c-114">See also</span></span>
