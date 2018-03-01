---
title: "ICorDebugFunction::GetNativeCode – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15383198da740f536061f1568fb06f042117b19c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="7ff2b-102">ICorDebugFunction::GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="7ff2b-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="7ff2b-103">Získá nativní kód pro funkce, která je reprezentována tuto instanci ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="7ff2b-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ff2b-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ff2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ff2b-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7ff2b-106">[out] Ukazatel na ICorDebugCode instanci, která reprezentuje nativní kód pro tuto funkci, nebo hodnota null, pokud je tato funkce Microsoft (MSIL intermediate language) kód, který nebyl v běhu (JIT) zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="7ff2b-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ff2b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ff2b-107">Remarks</span></span>  
 <span data-ttu-id="7ff2b-108">Pokud funkce, která je reprezentována to `ICorDebugFunction` instance byl kompilována více než jednou, jako v případě obecné typy `GetNativeCode` vrátí objekt náhodných nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="7ff2b-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff2b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ff2b-109">Requirements</span></span>  
 <span data-ttu-id="7ff2b-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff2b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff2b-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ff2b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ff2b-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ff2b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff2b-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff2b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
