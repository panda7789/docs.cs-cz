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
ms.openlocfilehash: da5acebb9cb90efa69b0f553a1480e5e6883d079
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="91ba1-102">ICorDebugProcess::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="91ba1-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="91ba1-103">Získá tento proces vlákno, které má ID zadaný operační systém (OS) vlákna.</span><span class="sxs-lookup"><span data-stu-id="91ba1-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ba1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91ba1-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91ba1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91ba1-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="91ba1-106">[v] ID podprocesu mají být načteny podprocesu operačního systému.</span><span class="sxs-lookup"><span data-stu-id="91ba1-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="91ba1-107">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="91ba1-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ba1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91ba1-108">Requirements</span></span>  
 <span data-ttu-id="91ba1-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ba1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ba1-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91ba1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91ba1-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91ba1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91ba1-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ba1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
