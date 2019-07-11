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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2779cfaecfdd241b5317ac8b467222e045d48049
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753317"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="6d44b-102">ICorDebugEval2::CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="6d44b-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="6d44b-103">Nastaví volání zadané ICorDebugFunction, které mohou být vnořené uvnitř třídy, jejíž konstruktor přijímá <xref:System.Type> parametry nebo může samotné trvat <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="6d44b-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d44b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d44b-104">Syntax</span></span>  
  
```cpp  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d44b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d44b-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="6d44b-106">[in] Ukazatel `ICorDebugFunction` objekt, který reprezentuje funkce, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="6d44b-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="6d44b-107">[in] Počet argumentů, které provede funkci.</span><span class="sxs-lookup"><span data-stu-id="6d44b-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="6d44b-108">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugType, který představuje argument funkce.</span><span class="sxs-lookup"><span data-stu-id="6d44b-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="6d44b-109">[in] Ve funkci byl předán počet hodnot.</span><span class="sxs-lookup"><span data-stu-id="6d44b-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="6d44b-110">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který představuje hodnotu předaného argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="6d44b-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d44b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d44b-111">Remarks</span></span>  
 <span data-ttu-id="6d44b-112">`CallParameterizedFunction` je třeba [icordebugeval::CallFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) s tím rozdílem, že funkce mohou být uvnitř třídy s parametry typu, samotné trvat parametry typu, nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="6d44b-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="6d44b-113">Argumenty typu by se měly provádět první třídy a funkce.</span><span class="sxs-lookup"><span data-stu-id="6d44b-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="6d44b-114">Pokud je funkce v různých aplikační domény, bude docházet k přechodu.</span><span class="sxs-lookup"><span data-stu-id="6d44b-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="6d44b-115">Nicméně všechny argumenty typu a hodnoty musí být v cílové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d44b-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="6d44b-116">Vyhodnocení funkce lze provést pouze v omezených scénářích.</span><span class="sxs-lookup"><span data-stu-id="6d44b-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="6d44b-117">Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrácená hodnota HRESULT označí nejobecnější důvod selhání.</span><span class="sxs-lookup"><span data-stu-id="6d44b-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d44b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d44b-118">Requirements</span></span>  
 <span data-ttu-id="6d44b-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d44b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d44b-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d44b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d44b-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d44b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d44b-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d44b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
