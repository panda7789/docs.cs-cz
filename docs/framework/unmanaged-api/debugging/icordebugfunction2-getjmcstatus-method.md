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
ms.openlocfilehash: 56dc5f87b32b3aaa0bfbb69541d5a01ae26606ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213228"
---
# <a name="icordebugfunction2getjmcstatus-method"></a><span data-ttu-id="8d9b4-102">ICorDebugFunction2::GetJMCStatus – metoda</span><span class="sxs-lookup"><span data-stu-id="8d9b4-102">ICorDebugFunction2::GetJMCStatus Method</span></span>
<span data-ttu-id="8d9b4-103">Získá hodnotu, která označuje, zda je funkce reprezentovaná tímto objektem ICorDebugFunction2 označena jako uživatelský kód.</span><span class="sxs-lookup"><span data-stu-id="8d9b4-103">Gets a value that indicates whether the function that is represented by this ICorDebugFunction2 object is marked as user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d9b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d9b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d9b4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d9b4-105">Parameters</span></span>  
 `pbIsJustMyCode`  
 <span data-ttu-id="8d9b4-106">mimo Ukazatel na logickou hodnotu, která je `true` , pokud je tato funkce označena jako kód uživatele; v opačném případě je hodnota `false` .</span><span class="sxs-lookup"><span data-stu-id="8d9b4-106">[out] A pointer to a Boolean value that is `true`, if this function is marked as user code; otherwise, the value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d9b4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d9b4-107">Remarks</span></span>  
 <span data-ttu-id="8d9b4-108">Pokud funkce reprezentovaná tímto typem `ICorDebugFunction2` nemůže být Laděna, `pbIsJustMyCode` bude vždy `false` .</span><span class="sxs-lookup"><span data-stu-id="8d9b4-108">If the function represented by this `ICorDebugFunction2` cannot be debugged, `pbIsJustMyCode` will always be `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d9b4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d9b4-109">Requirements</span></span>  
 <span data-ttu-id="8d9b4-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d9b4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d9b4-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8d9b4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d9b4-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d9b4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d9b4-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d9b4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
