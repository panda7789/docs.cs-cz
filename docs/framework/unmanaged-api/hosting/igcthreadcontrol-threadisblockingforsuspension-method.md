---
title: IGCThreadControl::ThreadIsBlockingForSuspension – metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134752"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="edf80-102">IGCThreadControl::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="edf80-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="edf80-103">Upozorní hostitele, že vlákno, které provádí volání, bude zablokované, třeba pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="edf80-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="edf80-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="edf80-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="edf80-105">Remarks</span></span>  
 <span data-ttu-id="edf80-106">Hostitel se může rozhodnout v rámci zpětného volání `ThreadIsBlockingForSuspension`, jestli se má vlákno znovu naplánovat.</span><span class="sxs-lookup"><span data-stu-id="edf80-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf80-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="edf80-107">Requirements</span></span>  
 <span data-ttu-id="edf80-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf80-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf80-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="edf80-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="edf80-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="edf80-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="edf80-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf80-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edf80-112">See also</span></span>

- [<span data-ttu-id="edf80-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="edf80-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
