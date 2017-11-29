---
title: "ICorDebugThread::GetProcess – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be58714856b93a244248fb97d6cc1e1b4ec476c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="8557b-102">ICorDebugThread::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="8557b-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="8557b-103">Získá ukazatele rozhraní pro proces, který tento ICorDebugThread součástí.</span><span class="sxs-lookup"><span data-stu-id="8557b-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8557b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8557b-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8557b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8557b-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="8557b-106">[out] Ukazatel na adresu ICorDebugProcess rozhraní objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="8557b-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8557b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8557b-107">Requirements</span></span>  
 <span data-ttu-id="8557b-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8557b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8557b-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8557b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8557b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8557b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8557b-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8557b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
