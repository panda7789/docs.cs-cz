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
ms.openlocfilehash: 59328c8b7e86694610de20ade72a98a4280b439d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762628"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="d921c-102">ICorDebugThread::GetActiveChain – metoda</span><span class="sxs-lookup"><span data-stu-id="d921c-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="d921c-103">Získá ukazatel rozhraní na tomto objektu icordebugthread – aktivní (nejnovější) řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d921c-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d921c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d921c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d921c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d921c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="d921c-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje řetěz zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d921c-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d921c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d921c-107">Remarks</span></span>  
 <span data-ttu-id="d921c-108">`ppChain` Parametr má hodnotu null, pokud žádné řetěz zásobníku není aktuálně aktivní.</span><span class="sxs-lookup"><span data-stu-id="d921c-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d921c-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d921c-109">Requirements</span></span>  
 <span data-ttu-id="d921c-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d921c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d921c-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d921c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d921c-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d921c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d921c-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d921c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
