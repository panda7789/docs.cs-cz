---
title: ICorDebugType::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791299"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="66497-102">ICorDebugType::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="66497-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="66497-103">Získá ukazatel rozhraní na ICorDebugClass, který představuje nevytvořený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="66497-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66497-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66497-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66497-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66497-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="66497-106">mimo Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje neinstanciující obecný typ.</span><span class="sxs-lookup"><span data-stu-id="66497-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66497-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66497-107">Remarks</span></span>  
 <span data-ttu-id="66497-108">`GetClass` lze volat pouze za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="66497-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="66497-109">Před voláním `GetClass`volejte [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="66497-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="66497-110">Pokud `ICorDebugType::GetType` vrátí hodnotu CorElementType –, která je ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` může být voláno pro získání neinstanceho typu pro obecný typ.</span><span class="sxs-lookup"><span data-stu-id="66497-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66497-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66497-111">Requirements</span></span>  
 <span data-ttu-id="66497-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66497-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66497-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66497-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66497-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66497-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66497-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66497-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
