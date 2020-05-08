---
title: ICorDebugChain::GetThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
ms.openlocfilehash: 28b54026c8743f31a420e164944f60709e2e271b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894370"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="abc50-102">ICorDebugChain::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="abc50-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="abc50-103">Získá fyzické vlákno, na kterém je tento řetěz volání součástí.</span><span class="sxs-lookup"><span data-stu-id="abc50-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abc50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abc50-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="abc50-106">mimo Ukazatel na objekt ICorDebugThread, který představuje fyzické vlákno, na kterém je tento řetěz volání součástí.</span><span class="sxs-lookup"><span data-stu-id="abc50-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc50-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abc50-107">Requirements</span></span>  
 <span data-ttu-id="abc50-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc50-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc50-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="abc50-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abc50-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="abc50-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abc50-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc50-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
