---
title: "ICorDebugThread::GetID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 31ae48d62221d45a8457c304a1929886738190c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="56a37-102">ICorDebugThread::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="56a37-102">ICorDebugThread::GetID Method</span></span>
<span data-ttu-id="56a37-103">Získá aktuální identifikátor active součástí této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="56a37-103">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56a37-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56a37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56a37-105">Parameters</span></span>  
 `pdwThreadId`  
 <span data-ttu-id="56a37-106">[out] Identifikátor vlákno.</span><span class="sxs-lookup"><span data-stu-id="56a37-106">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56a37-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56a37-107">Remarks</span></span>  
 <span data-ttu-id="56a37-108">Identifikátor operačního systému by mohl změnit během spuštění procesu a může být jinou hodnotu pro různé části vlákno.</span><span class="sxs-lookup"><span data-stu-id="56a37-108">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56a37-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56a37-109">Requirements</span></span>  
 <span data-ttu-id="56a37-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56a37-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a37-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56a37-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56a37-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56a37-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56a37-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a37-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
