---
title: "ICorDebugEval2::CallParameterizedFunction – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.CallParameterizedFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 720d9c4fb9b997538ee2bb18ac7987350f6bfb57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2callparameterizedfunction-method"></a><span data-ttu-id="38e65-102">ICorDebugEval2::CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="38e65-102">ICorDebugEval2::CallParameterizedFunction Method</span></span>
<span data-ttu-id="38e65-103">Nastavuje volání do zadané ICorDebugFunction, což může být vnořena ve třídu, jejíž konstruktor přijímá <xref:System.Type> parametry, nebo může sám sebe trvat <xref:System.Type> parametry.</span><span class="sxs-lookup"><span data-stu-id="38e65-103">Sets up a call to the specified ICorDebugFunction, which can be nested inside a class whose constructor takes <xref:System.Type> parameters, or can itself take <xref:System.Type> parameters.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e65-104">Syntax</span></span>  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38e65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38e65-105">Parameters</span></span>  
 `pFunction`  
 <span data-ttu-id="38e65-106">[v] Ukazatel na `ICorDebugFunction` objekt, který reprezentuje funkce, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="38e65-106">[in] A pointer to an `ICorDebugFunction` object that represents the function to be called.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="38e65-107">[v] Počet argumentů, které funkce přijímá.</span><span class="sxs-lookup"><span data-stu-id="38e65-107">[in] The number of arguments that the function takes.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="38e65-108">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který představuje argument funkce.</span><span class="sxs-lookup"><span data-stu-id="38e65-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a function argument.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="38e65-109">[v] Počet hodnot, je předaná funkci.</span><span class="sxs-lookup"><span data-stu-id="38e65-109">[in] The number of values passed in the function.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="38e65-110">[v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugValue, který reprezentuje hodnotu předáno v argumentu funkce.</span><span class="sxs-lookup"><span data-stu-id="38e65-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents a value passed in a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38e65-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38e65-111">Remarks</span></span>  
 <span data-ttu-id="38e65-112">`CallParameterizedFunction`je třeba [icordebugeval::CallFunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) s tím rozdílem, že funkce může být uvnitř tříd pomocí parametrů typu, může sám sebe trvat parametry typu nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="38e65-112">`CallParameterizedFunction` is like [ICorDebugEval::CallFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md) except that the function may be inside a class with type parameters, may itself take type parameters, or both.</span></span> <span data-ttu-id="38e65-113">Argumenty typu by měly mít nejprve pro třídu a potom pro funkci.</span><span class="sxs-lookup"><span data-stu-id="38e65-113">The type arguments should be given first for the class, and then for the function.</span></span>  
  
 <span data-ttu-id="38e65-114">Pokud je v doméně jinou aplikaci, dojde k přechodu.</span><span class="sxs-lookup"><span data-stu-id="38e65-114">If the function is in a different application domain, a transition will occur.</span></span> <span data-ttu-id="38e65-115">Všechny argumenty typu a hodnoty musí však být v cílové doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="38e65-115">However, all type and value arguments must be in the target application domain.</span></span>  
  
 <span data-ttu-id="38e65-116">Vyhodnocení funkce lze provést jenom v situacích, omezené.</span><span class="sxs-lookup"><span data-stu-id="38e65-116">Function evaluation can be performed only in limited scenarios.</span></span> <span data-ttu-id="38e65-117">Pokud `CallParameterizedFunction` nebo `ICorDebugEval::CallFunction` selže, vrácený HRESULT označí nejobecnější možný důvod selhání.</span><span class="sxs-lookup"><span data-stu-id="38e65-117">If `CallParameterizedFunction` or `ICorDebugEval::CallFunction` fails, the returned HRESULT will indicate the most general possible reason for failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e65-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38e65-118">Requirements</span></span>  
 <span data-ttu-id="38e65-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38e65-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e65-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38e65-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38e65-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38e65-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38e65-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e65-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
