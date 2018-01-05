---
title: "ICorDebugProcess::GetThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 996003f254c5150dfd39ca62d7cadf07282596c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="2fd21-102">ICorDebugProcess::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="2fd21-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="2fd21-103">Získá tento proces vlákno, které má ID zadaný operační systém (OS) vlákna.</span><span class="sxs-lookup"><span data-stu-id="2fd21-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fd21-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2fd21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fd21-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="2fd21-106">[v] ID podprocesu mají být načteny podprocesu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2fd21-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="2fd21-107">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="2fd21-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd21-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2fd21-108">Requirements</span></span>  
 <span data-ttu-id="2fd21-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fd21-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd21-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fd21-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd21-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd21-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd21-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd21-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
