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
ms.openlocfilehash: b05f5a3f29c7b72ed83c1456175f68ef9b986e3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987180"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="d84eb-102">ICorDebugThread::GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="d84eb-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="d84eb-103">Získá ukazatel rozhraní na tomto objektu icordebugthread – aktivní (nejnovější) řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d84eb-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d84eb-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d84eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d84eb-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d84eb-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d84eb-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d84eb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d84eb-107">Remarks</span></span>  
 <span data-ttu-id="d84eb-108">`ppChain` Parametr má hodnotu null, pokud žádné řetěz zásobníku není aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="d84eb-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84eb-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d84eb-109">Requirements</span></span>  
 <span data-ttu-id="d84eb-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d84eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d84eb-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d84eb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d84eb-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d84eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d84eb-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d84eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
