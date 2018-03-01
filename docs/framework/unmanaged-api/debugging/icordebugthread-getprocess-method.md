---
title: "ICorDebugThread::GetProcess – metoda"
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
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 04410024dfe145b7df96dc0f3d8df6fab230f2c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="7d003-102">ICorDebugThread::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="7d003-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="7d003-103">Získá ukazatele rozhraní pro proces, který tento ICorDebugThread součástí.</span><span class="sxs-lookup"><span data-stu-id="7d003-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d003-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d003-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d003-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d003-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="7d003-106">[out] Ukazatel na adresu ICorDebugProcess rozhraní objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="7d003-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d003-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d003-107">Requirements</span></span>  
 <span data-ttu-id="7d003-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d003-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d003-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d003-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d003-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d003-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d003-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d003-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
