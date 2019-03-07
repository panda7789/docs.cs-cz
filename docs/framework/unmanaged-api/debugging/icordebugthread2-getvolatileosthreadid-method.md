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
ms.openlocfilehash: a9bf96371798b38bc392bc6bbd8f6fe8f97c7969
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501965"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="26a91-102">ICorDebugThread2::GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="26a91-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="26a91-103">Získá identifikátor vlákna operačního systému pro toto icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="26a91-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26a91-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26a91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26a91-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="26a91-106">[out] Identifikátor vlákna operačního systému pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="26a91-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26a91-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26a91-107">Requirements</span></span>  
 <span data-ttu-id="26a91-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26a91-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26a91-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26a91-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26a91-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26a91-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26a91-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26a91-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
