---
title: ICorDebugThread2::GetVolatileOSThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d964a5a77569762ff4fd69e419324a377b820d97
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768944"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="b91f6-102">ICorDebugThread2::GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="b91f6-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="b91f6-103">Získá identifikátor vlákna operačního systému pro toto icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="b91f6-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b91f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b91f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b91f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b91f6-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="b91f6-106">[out] Identifikátor vlákna operačního systému pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="b91f6-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b91f6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b91f6-107">Requirements</span></span>  
 <span data-ttu-id="b91f6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b91f6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b91f6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b91f6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b91f6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b91f6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b91f6-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b91f6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
