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
ms.openlocfilehash: 1cf0080945ad78565fae3fedb454ceba7825cb4a
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976236"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="75164-102">ICorDebugEval::CallFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="75164-102">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="75164-103">Nastaví volání zadané funkce.</span><span class="sxs-lookup"><span data-stu-id="75164-103">Sets up a call to the specified function.</span></span>

<span data-ttu-id="75164-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="75164-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="75164-105">Místo toho použijte [ICorDebugEval2:: CallParameterizedFunction –](icordebugeval2-callparameterizedfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="75164-105">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="75164-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75164-106">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="75164-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="75164-107">Parameters</span></span>

`pFunction`\
<span data-ttu-id="75164-108">pro Ukazatel na objekt ICorDebugFunction, který určuje funkci, která má být volána.</span><span class="sxs-lookup"><span data-stu-id="75164-108">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="75164-109">pro Počet argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="75164-109">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="75164-110">pro Pole ukazatelů, z nichž každý odkazuje na objekt ICorDebugValue, který určuje argument, který má být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="75164-110">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="75164-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75164-111">Remarks</span></span>

<span data-ttu-id="75164-112">Pokud je funkce virtuální, `CallFunction` provede virtuální odeslání.</span><span class="sxs-lookup"><span data-stu-id="75164-112">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="75164-113">Pokud je funkce v jiné doméně aplikace, přechod bude proveden, pokud jsou všechny argumenty také v dané doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="75164-113">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="75164-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75164-114">Requirements</span></span>

<span data-ttu-id="75164-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75164-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="75164-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75164-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="75164-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="75164-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="75164-118">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="75164-118">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="75164-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="75164-119">See also</span></span>

- [<span data-ttu-id="75164-120">CallParameterizedFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="75164-120">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
