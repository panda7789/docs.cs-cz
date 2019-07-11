---
title: ICorDebugProcess::GetThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5cbdd19fa14a41d8bd2eadec80dbafcea7b720d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766441"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="b0065-102">ICorDebugProcess::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="b0065-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="b0065-103">Získá tento proces vlákna, která má ID vlákna. Zadaný operační systém (OS)</span><span class="sxs-lookup"><span data-stu-id="b0065-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0065-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0065-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0065-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0065-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="b0065-106">[in] Operační systém vlákna ID vlákna, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="b0065-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="b0065-107">[out] Ukazatel na adresu icordebugthread – objekt, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="b0065-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0065-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0065-108">Requirements</span></span>  
 <span data-ttu-id="b0065-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0065-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0065-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0065-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0065-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0065-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0065-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0065-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
