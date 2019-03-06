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
ms.openlocfilehash: 66e51dc15f7d44ede26634571fa04c58e9735694
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364148"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="6b8ba-102">ICorDebugEval::CallFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="6b8ba-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="6b8ba-103">Nastaví zadanou funkci volání.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="6b8ba-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6b8ba-105">Použití [icordebugeval2::callparameterizedfunction –](icordebugeval2-callparameterizedfunction-method.md) místo.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b8ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b8ba-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="6b8ba-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b8ba-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="6b8ba-108">[in] Ukazatel na objekt ICorDebugFunction, který určuje funkci, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="6b8ba-109">[in] Počet argumentů pro funkce.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="6b8ba-110">[in] Pole ukazatelů, každý z nich odkazuje na objekt ICorDebugValue, který určuje argument předaný do funkce.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b8ba-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b8ba-111">Remarks</span></span>

<span data-ttu-id="6b8ba-112">Pokud je virtuální, funkce `CallFunction` provede virtuální odeslání.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="6b8ba-113">Pokud je funkce v různých aplikační domény, přechod dojde, pokud jsou všechny argumenty také v této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b8ba-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="6b8ba-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b8ba-114">Requirements</span></span>

<span data-ttu-id="6b8ba-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b8ba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6b8ba-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b8ba-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="6b8ba-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b8ba-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6b8ba-118">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="6b8ba-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="6b8ba-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b8ba-119">See also</span></span>

- [<span data-ttu-id="6b8ba-120">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="6b8ba-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)