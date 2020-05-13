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
ms.openlocfilehash: 878a57514af34730049864f17f4853c1237904c2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379963"
---
# <a name="icordebugtypegetclass-method"></a><span data-ttu-id="04035-102">ICorDebugType::GetClass – metoda</span><span class="sxs-lookup"><span data-stu-id="04035-102">ICorDebugType::GetClass Method</span></span>
<span data-ttu-id="04035-103">Získá ukazatel rozhraní na ICorDebugClass, který představuje nevytvořený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="04035-103">Gets an interface pointer to an ICorDebugClass that represents the uninstantiated generic type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04035-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04035-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04035-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04035-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="04035-106">mimo Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje neinstanciující obecný typ.</span><span class="sxs-lookup"><span data-stu-id="04035-106">[out] A pointer to the address of an `ICorDebugClass` interface that represents the uninstantiated generic type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04035-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04035-107">Remarks</span></span>  
 <span data-ttu-id="04035-108">`GetClass`dá se volat jenom za určitých podmínek.</span><span class="sxs-lookup"><span data-stu-id="04035-108">`GetClass` can be called only under certain conditions.</span></span> <span data-ttu-id="04035-109">Před voláním volejte [ICorDebugType:: GetType](icordebugtype-gettype-method.md) `GetClass` .</span><span class="sxs-lookup"><span data-stu-id="04035-109">Call [ICorDebugType::GetType](icordebugtype-gettype-method.md) before calling `GetClass`.</span></span> <span data-ttu-id="04035-110">Pokud `ICorDebugType::GetType` vrátí hodnotu CorElementType –, která je ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` lze volat pro získání typu bez instance pro obecný typ.</span><span class="sxs-lookup"><span data-stu-id="04035-110">If `ICorDebugType::GetType` returns a CorElementType value that is ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, `GetClass` can be called to get the uninstantiated type for a generic type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04035-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04035-111">Requirements</span></span>  
 <span data-ttu-id="04035-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04035-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04035-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="04035-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04035-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="04035-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04035-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04035-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
