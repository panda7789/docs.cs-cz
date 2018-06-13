---
title: ICorDebugThread::GetActiveChain – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9030319ca12aafcf452e3ecd816fc269f0abfc0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417512"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="952cf-102">ICorDebugThread::GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="952cf-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="952cf-103">Získá ukazatele rozhraní k řetězu active zásobníku (nejnovější) na tomto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="952cf-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="952cf-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="952cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="952cf-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="952cf-106">[out] Ukazatel na adresu ICorDebugChain objekt, který reprezentuje řetězu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="952cf-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="952cf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="952cf-107">Remarks</span></span>  
 <span data-ttu-id="952cf-108">`ppChain` Parametr má hodnotu null, pokud je aktuálně aktivní žádné řetězec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="952cf-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="952cf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="952cf-109">Requirements</span></span>  
 <span data-ttu-id="952cf-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952cf-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="952cf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="952cf-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="952cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="952cf-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
