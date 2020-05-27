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
ms.openlocfilehash: b5f6d7d40274972438a01313bc6aaec475b8e0c6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805093"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="84060-102">IGCThreadControl::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="84060-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="84060-103">Upozorní hostitele, že vlákno, které provádí volání, bude zablokované, třeba pro uvolňování paměti nebo jiné pozastavení.</span><span class="sxs-lookup"><span data-stu-id="84060-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84060-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84060-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="84060-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84060-105">Remarks</span></span>  
 <span data-ttu-id="84060-106">Hostitel se může rozhodnout v rámci `ThreadIsBlockingForSuspension` zpětného volání, bez ohledu na to, jestli má vlákno znovu naplánovat.</span><span class="sxs-lookup"><span data-stu-id="84060-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84060-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="84060-107">Requirements</span></span>  
 <span data-ttu-id="84060-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84060-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84060-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="84060-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84060-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="84060-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84060-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84060-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84060-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="84060-112">See also</span></span>

- [<span data-ttu-id="84060-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="84060-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
