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
ms.openlocfilehash: e8d59d617efa7656a3034d5c5e009a46b6121cdb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377663"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="bb24f-102">ICorDebugThread2::GetVolatileOSThreadID – metoda</span><span class="sxs-lookup"><span data-stu-id="bb24f-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="bb24f-103">Získá identifikátor vlákna operačního systému pro tento ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="bb24f-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb24f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb24f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb24f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb24f-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="bb24f-106">mimo Identifikátor vlákna operačního systému pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="bb24f-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb24f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bb24f-107">Requirements</span></span>  
 <span data-ttu-id="bb24f-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb24f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb24f-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bb24f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb24f-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb24f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb24f-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb24f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
