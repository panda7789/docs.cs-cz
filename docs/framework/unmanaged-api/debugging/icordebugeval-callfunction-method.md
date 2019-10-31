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
ms.openlocfilehash: 4ac26ef4449dc02230f26b1247616b4587d217b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085162"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="276b0-102">ICorDebugEval::CallFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="276b0-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="276b0-103">Nastaví volání zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="276b0-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="276b0-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="276b0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="276b0-105">Místo toho použijte [ICorDebugEval2:: CallParameterizedFunction –](icordebugeval2-callparameterizedfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="276b0-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="276b0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="276b0-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="276b0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="276b0-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="276b0-108">pro Ukazatel na objekt ICorDebugFunction, který určuje funkci, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="276b0-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="276b0-109">pro Počet argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="276b0-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="276b0-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který určuje argument, který má být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="276b0-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="276b0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="276b0-111">Remarks</span></span>

<span data-ttu-id="276b0-112">Pokud je funkce virtuální, `CallFunction` provede virtuální odeslání.</span><span class="sxs-lookup"><span data-stu-id="276b0-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="276b0-113">Pokud je funkce v jiné doméně aplikace, přechod bude proveden, pokud jsou všechny argumenty také v dané doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="276b0-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="276b0-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="276b0-114">Requirements</span></span>

<span data-ttu-id="276b0-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="276b0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="276b0-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="276b0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="276b0-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="276b0-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="276b0-118">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="276b0-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="276b0-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="276b0-119">See also</span></span>

- [<span data-ttu-id="276b0-120">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="276b0-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
