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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8609b32ad2dea699b5b248b2b8bb3d81ec744043
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779472"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="8f8a5-102">IGCThreadControl::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="8f8a5-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="8f8a5-103">Upozorňuje hostitele, že vlákno, které provádí volání se chystáte se zablokovat, případně pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="8f8a5-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f8a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f8a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="8f8a5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f8a5-105">Remarks</span></span>  
 <span data-ttu-id="8f8a5-106">Zvolit hostitele v rámci `ThreadIsBlockingForSuspension` zpětné volání, jestli se má plánovanou zkoušku přeplánovat vlákno.</span><span class="sxs-lookup"><span data-stu-id="8f8a5-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f8a5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8f8a5-107">Requirements</span></span>  
 <span data-ttu-id="8f8a5-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f8a5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8a5-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f8a5-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f8a5-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f8a5-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f8a5-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8a5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8a5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f8a5-112">See also</span></span>

- [<span data-ttu-id="8f8a5-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8f8a5-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
