---
title: ICorDebugArrayValue::GetElement – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179013"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="8cad8-102">ICorDebugArrayValue::GetElement – metoda</span><span class="sxs-lookup"><span data-stu-id="8cad8-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="8cad8-103">Získá hodnotu daného prvku pole.</span><span class="sxs-lookup"><span data-stu-id="8cad8-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cad8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cad8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cad8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cad8-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="8cad8-106">[v] Počet rozměrů tohoto `ICorDebugArrayValue` objektu.</span><span class="sxs-lookup"><span data-stu-id="8cad8-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="8cad8-107">Tato hodnota je také `indices` velikost pole, protože jeho velikost se rovná `ICorDebugArrayValue` počtu dimenzí objektu.</span><span class="sxs-lookup"><span data-stu-id="8cad8-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="8cad8-108">[v] Pole hodnot indexu, z nichž každá určuje pozici v `ICorDebugArrayValue` rámci dimenze objektu.</span><span class="sxs-lookup"><span data-stu-id="8cad8-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="8cad8-109">Tato hodnota nesmí být null.</span><span class="sxs-lookup"><span data-stu-id="8cad8-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8cad8-110">[out] Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu zadaného prvku.</span><span class="sxs-lookup"><span data-stu-id="8cad8-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cad8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cad8-111">Requirements</span></span>  
 <span data-ttu-id="8cad8-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cad8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cad8-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cad8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cad8-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cad8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cad8-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cad8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
