---
title: ICorDebugEval2::CallParameterizedFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
ms.openlocfilehash: b521c96d26202119dad6fedb61cbd9da8b3c2e52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137628"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="2113a-102">ICorDebugEval2::CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="2113a-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="2113a-103">Nastaví volání na zadaný ICorDebugFunction, který může být vnořen do třídy, jejíž konstruktor přebírá parametry <xref:System.Type>, nebo může přebírat <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="2113a-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2113a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2113a-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2113a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2113a-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="2113a-106">pro Ukazatel na objekt `ICorDebugFunction`, který představuje funkci, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="2113a-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="2113a-107">pro Počet argumentů, které funkce trvá.</span><span class="sxs-lookup"><span data-stu-id="2113a-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="2113a-108">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument funkce.</span><span class="sxs-lookup"><span data-stu-id="2113a-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="2113a-109">pro Počet hodnot předaných ve funkci.</span><span class="sxs-lookup"><span data-stu-id="2113a-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="2113a-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který představuje hodnotu předanou v argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="2113a-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2113a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2113a-111">Remarks</span></span>  
 <span data-ttu-id="2113a-112">`CallParameterizedFunction` jako [ICorDebugEval:: CallFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) s tím rozdílem, že funkce může být uvnitř třídy s parametry typu, může sám převzít parametry typu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="2113a-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="2113a-113">Argumenty typu by měly být zadány jako první pro třídu a potom pro funkci.</span><span class="sxs-lookup"><span data-stu-id="2113a-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="2113a-114">Pokud je funkce v jiné doméně aplikace, dojde k přechodu.</span><span class="sxs-lookup"><span data-stu-id="2113a-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="2113a-115">Všechny argumenty Type a Value však musí být v cílové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2113a-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="2113a-116">Vyhodnocení funkce se dá provádět jenom v omezených scénářích.</span><span class="sxs-lookup"><span data-stu-id="2113a-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="2113a-117">Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrátí vrácená hodnota HRESULT nejobecnější možný důvod selhání.</span><span class="sxs-lookup"><span data-stu-id="2113a-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2113a-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2113a-118">Requirements</span></span>  
 <span data-ttu-id="2113a-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2113a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2113a-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2113a-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2113a-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2113a-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2113a-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2113a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
