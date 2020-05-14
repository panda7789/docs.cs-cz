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
ms.openlocfilehash: dcec97bac2aefc8db1f9351f1dacb0f36fc0d2a0
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396796"
---
# <a name="icordebugvalue2getexacttype-method"></a><span data-ttu-id="71d51-102">ICorDebugValue2::GetExactType – metoda</span><span class="sxs-lookup"><span data-stu-id="71d51-102">ICorDebugValue2::GetExactType Method</span></span>
<span data-ttu-id="71d51-103">Získá ukazatel rozhraní na objekt "ICorDebugType", který představuje <xref:System.Type> tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71d51-103">Gets an interface pointer to an "ICorDebugType" object that represents the <xref:System.Type> of this value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d51-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71d51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d51-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71d51-105">Parameters</span></span>  
 `ppType`  
 <span data-ttu-id="71d51-106">mimo Ukazatel na adresu `ICorDebugType` objektu, který představuje <xref:System.Type> hodnotu reprezentovanou tímto objektem "ICorDebugValue2".</span><span class="sxs-lookup"><span data-stu-id="71d51-106">[out] A pointer to the address of an `ICorDebugType` object that represents the <xref:System.Type> of the value represented by this "ICorDebugValue2" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71d51-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71d51-107">Remarks</span></span>  
 <span data-ttu-id="71d51-108">Metoda zohledňující obecné `GetExactType` metody nahrazuje obě metody [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) a [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , z nichž každý vrací informace o typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="71d51-108">The generics-aware `GetExactType` method supersedes both the [ICorDebugObjectValue::GetClass](icordebugobjectvalue-getclass-method.md) and the [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods, each of which return information about the type of a value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d51-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71d51-109">Requirements</span></span>  
 <span data-ttu-id="71d51-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d51-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d51-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71d51-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71d51-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="71d51-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71d51-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d51-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="71d51-114">See also</span></span>
