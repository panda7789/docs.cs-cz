---
title: "IGCThreadControl::ThreadIsBlockingForSuspension – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.ThreadIsBlockingForSuspension
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0cb7cfbab18334f1892c24225311160179920f81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="fe055-102">IGCThreadControl::ThreadIsBlockingForSuspension – metoda</span><span class="sxs-lookup"><span data-stu-id="fe055-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="fe055-103">Upozorní hostitele, že vlákno, které je uskutečněním hovoru se chystáte se zablokovat, případně pro uvolnění paměti nebo jiných pozastavení.</span><span class="sxs-lookup"><span data-stu-id="fe055-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe055-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe055-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fe055-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe055-105">Remarks</span></span>  
 <span data-ttu-id="fe055-106">Hostitel rozhodnout, že v rámci `ThreadIsBlockingForSuspension` zpětného volání jestli se má změnit plán naplánovaných vlákna.</span><span class="sxs-lookup"><span data-stu-id="fe055-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe055-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe055-107">Requirements</span></span>  
 <span data-ttu-id="fe055-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe055-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe055-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fe055-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe055-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe055-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe055-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe055-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe055-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe055-112">See Also</span></span>  
 [<span data-ttu-id="fe055-113">IGCThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe055-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
