---
title: ICorDebugThread::GetProcess – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b41c7eeccad8b3f685c81e6afc23eaf19d862182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417609"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="e12b8-102">ICorDebugThread::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="e12b8-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="e12b8-103">Získá ukazatele rozhraní pro proces, který tento ICorDebugThread součástí.</span><span class="sxs-lookup"><span data-stu-id="e12b8-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e12b8-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e12b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e12b8-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="e12b8-106">[out] Ukazatel na adresu ICorDebugProcess rozhraní objekt, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="e12b8-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e12b8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e12b8-107">Requirements</span></span>  
 <span data-ttu-id="e12b8-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e12b8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e12b8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e12b8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e12b8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e12b8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e12b8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12b8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
