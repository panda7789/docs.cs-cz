---
title: ICorDebugEval::CallFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65225281fe3abaa20e69e96f4cd4d2a4b03a87ce
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629945"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="5ef88-102">ICorDebugEval::CallFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="5ef88-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="5ef88-103">Nastaví zadanou funkci volání.</span><span class="sxs-lookup"><span data-stu-id="5ef88-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="5ef88-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="5ef88-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5ef88-105">Použití [icordebugeval2::callparameterizedfunction –](icordebugeval2-callparameterizedfunction-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="5ef88-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ef88-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ef88-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="5ef88-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="5ef88-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="5ef88-108">[in] Ukazatel na objekt ICorDebugFunction, který určuje funkci, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="5ef88-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="5ef88-109">[in] Počet argumentů pro funkce.</span><span class="sxs-lookup"><span data-stu-id="5ef88-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="5ef88-110">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který určuje argument předaný do funkce.</span><span class="sxs-lookup"><span data-stu-id="5ef88-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ef88-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ef88-111">Remarks</span></span>

<span data-ttu-id="5ef88-112">Pokud je virtuální, funkce `CallFunction` provede virtuální odeslání.</span><span class="sxs-lookup"><span data-stu-id="5ef88-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="5ef88-113">Pokud je funkce v různých aplikační domény, přechod dojde, pokud jsou všechny argumenty také v této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="5ef88-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ef88-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ef88-114">Requirements</span></span>

<span data-ttu-id="5ef88-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef88-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5ef88-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ef88-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5ef88-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ef88-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ef88-118">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="5ef88-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef88-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ef88-119">See also</span></span>

- [<span data-ttu-id="5ef88-120">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="5ef88-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
