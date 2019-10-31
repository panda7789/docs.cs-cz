---
title: ICorDebugFunction2::GetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137809"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="333c1-102">ICorDebugFunction2::GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="333c1-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="333c1-103">Získá hodnotu, která označuje, zda je funkce reprezentovaná tímto objektem ICorDebugFunction2 označena jako uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="333c1-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="333c1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="333c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="333c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="333c1-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="333c1-106">mimo Ukazatel na logickou hodnotu, která je `true`, pokud je tato funkce označena jako kód uživatele; v opačném případě je hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="333c1-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="333c1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="333c1-107">Remarks</span></span>  
 <span data-ttu-id="333c1-108">Pokud funkce reprezentovaná tímto `ICorDebugFunction2` nemůže být Laděna, `pbIsJustMyCode` bude vždy `false`.</span><span class="sxs-lookup"><span data-stu-id="333c1-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="333c1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="333c1-109">Requirements</span></span>  
 <span data-ttu-id="333c1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="333c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="333c1-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="333c1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="333c1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="333c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="333c1-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="333c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
