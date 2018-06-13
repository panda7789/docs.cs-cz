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
ms.openlocfilehash: e1cb073c1f93c6d60d86e5160dcfb0cbdaf1cd33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414568"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="01596-102">ICorDebugFunction::GetNativeCode – metoda</span><span class="sxs-lookup"><span data-stu-id="01596-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="01596-103">Získá nativní kód pro funkce, která je reprezentována tuto instanci ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="01596-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01596-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01596-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01596-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01596-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="01596-106">[out] Ukazatel na ICorDebugCode instanci, která reprezentuje nativní kód pro tuto funkci, nebo hodnota null, pokud je tato funkce Microsoft (MSIL intermediate language) kód, který nebyl v běhu (JIT) zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="01596-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01596-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01596-107">Remarks</span></span>  
 <span data-ttu-id="01596-108">Pokud funkce, která je reprezentována to `ICorDebugFunction` instance byl kompilována více než jednou, jako v případě obecné typy `GetNativeCode` vrátí objekt náhodných nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="01596-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01596-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01596-109">Requirements</span></span>  
 <span data-ttu-id="01596-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01596-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01596-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01596-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01596-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01596-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01596-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01596-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
