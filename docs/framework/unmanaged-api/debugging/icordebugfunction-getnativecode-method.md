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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb85c4b2c26c136a5f9fc05221a42c4bc99f37f9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470169"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="6a9fd-102">ICorDebugFunction::GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="6a9fd-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="6a9fd-103">Získá nativní kód pro funkce, který je reprezentovaný touto instancí ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="6a9fd-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a9fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a9fd-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a9fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a9fd-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="6a9fd-106">[out] Ukazatel na ICorDebugCode instanci, která představuje nativní kód pro tuto funkci, nebo hodnota null, pokud je tato funkce Microsoft intermediate language (MSIL) kód, který nebyl just-in-time (JIT) zkompilována.</span><span class="sxs-lookup"><span data-stu-id="6a9fd-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a9fd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a9fd-107">Remarks</span></span>  
 <span data-ttu-id="6a9fd-108">Pokud funkce, která je reprezentována tímto objektem `ICorDebugFunction` instance byl zkompilován JIT Kompilátorem více než jednou, třeba v případě obecných typů `GetNativeCode` vrátí objekt náhodné nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="6a9fd-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a9fd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a9fd-109">Requirements</span></span>  
 <span data-ttu-id="6a9fd-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a9fd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a9fd-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a9fd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a9fd-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a9fd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a9fd-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a9fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
