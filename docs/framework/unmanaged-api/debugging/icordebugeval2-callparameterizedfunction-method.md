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
ms.openlocfilehash: ab31ab8f83a71372c8e12b460458a26996f65ff5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782978"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="d7a89-102">ICorDebugEval2::CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="d7a89-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="d7a89-103">Nastaví volání na zadaný ICorDebugFunction, který může být vnořen do třídy, jejíž konstruktor přebírá parametry <xref:System.Type>, nebo může přebírat <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="d7a89-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7a89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a89-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7a89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7a89-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="d7a89-106">pro Ukazatel na objekt `ICorDebugFunction`, který představuje funkci, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="d7a89-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="d7a89-107">pro Počet argumentů, které funkce trvá.</span><span class="sxs-lookup"><span data-stu-id="d7a89-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="d7a89-108">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugType, který představuje argument funkce.</span><span class="sxs-lookup"><span data-stu-id="d7a89-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="d7a89-109">pro Počet hodnot předaných ve funkci.</span><span class="sxs-lookup"><span data-stu-id="d7a89-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="d7a89-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který představuje hodnotu předanou v argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="d7a89-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7a89-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7a89-111">Remarks</span></span>  
 <span data-ttu-id="d7a89-112">`CallParameterizedFunction` jako [ICorDebugEval:: CallFunction –](icordebugeval-callfunction-method.md) s tím rozdílem, že funkce může být uvnitř třídy s parametry typu, může sám převzít parametry typu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="d7a89-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="d7a89-113">Argumenty typu by měly být zadány jako první pro třídu a potom pro funkci.</span><span class="sxs-lookup"><span data-stu-id="d7a89-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="d7a89-114">Pokud je funkce v jiné doméně aplikace, dojde k přechodu.</span><span class="sxs-lookup"><span data-stu-id="d7a89-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="d7a89-115">Všechny argumenty Type a Value však musí být v cílové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d7a89-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="d7a89-116">Vyhodnocení funkce se dá provádět jenom v omezených scénářích.</span><span class="sxs-lookup"><span data-stu-id="d7a89-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="d7a89-117">Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrátí vrácená hodnota HRESULT nejobecnější možný důvod selhání.</span><span class="sxs-lookup"><span data-stu-id="d7a89-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7a89-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7a89-118">Requirements</span></span>  
 <span data-ttu-id="d7a89-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7a89-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7a89-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7a89-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7a89-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d7a89-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7a89-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7a89-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
