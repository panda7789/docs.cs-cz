---
title: ICorDebugThread::GetID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52962ea7d2cf3dd1822b1a36cc6cfcb56bc427f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417190"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="7f68a-102">ICorDebugThread::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="7f68a-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="7f68a-103">Získá aktuální identifikátor active součástí této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="7f68a-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f68a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f68a-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f68a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f68a-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="7f68a-106">[out] Identifikátor vlákno.</span><span class="sxs-lookup"><span data-stu-id="7f68a-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f68a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f68a-107">Remarks</span></span>  
 <span data-ttu-id="7f68a-108">Identifikátor operačního systému by mohl změnit během spuštění procesu a může být jinou hodnotu pro různé části vlákno.</span><span class="sxs-lookup"><span data-stu-id="7f68a-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f68a-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f68a-109">Requirements</span></span>  
 <span data-ttu-id="7f68a-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f68a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f68a-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f68a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f68a-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f68a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f68a-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f68a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
