---
title: ICorDebugFunction::GetNativeCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 5bb41b2b49922475550997f18832b391522e2f26
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137861"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="cb1f1-102">ICorDebugFunction::GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="cb1f1-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="cb1f1-103">Získá nativní kód pro funkci, která je reprezentovaná touto instancí ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="cb1f1-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb1f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb1f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb1f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb1f1-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="cb1f1-106">mimo Ukazatel na instanci ICorDebugCode, která představuje nativní kód pro tuto funkci, nebo hodnotu null, pokud je tato funkce kód jazyka MSIL (Microsoft Intermediate Language), který nebyl zkompilován za běhu (just-in-time).</span><span class="sxs-lookup"><span data-stu-id="cb1f1-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb1f1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb1f1-107">Remarks</span></span>  
 <span data-ttu-id="cb1f1-108">Pokud byla funkce reprezentovaná touto `ICorDebugFunction` instancí zkompilována více než jednou, jako u obecných typů, `GetNativeCode` vrátí objekt náhodného nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="cb1f1-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb1f1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb1f1-109">Requirements</span></span>  
 <span data-ttu-id="cb1f1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb1f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb1f1-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cb1f1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb1f1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb1f1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb1f1-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb1f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
