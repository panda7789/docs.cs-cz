---
title: "IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a087dbcff961ca1ac1cf03d30fdc336ec9ca0515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="3c189-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="3c189-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="3c189-103">Upozorní hostitele, zda chcete uvolnit všechny vláken, která jsou blokovaná jsou ladění služby.</span><span class="sxs-lookup"><span data-stu-id="3c189-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c189-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c189-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="3c189-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c189-105">Remarks</span></span>  
 <span data-ttu-id="3c189-106">`ReleaseAllRuntimeThreads` Metoda nebude nikdy volat v podprocesu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3c189-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="3c189-107">Pokud má hostitel podprocesu modulu runtime blokované, ho měli je verze nyní.</span><span class="sxs-lookup"><span data-stu-id="3c189-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c189-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c189-108">Requirements</span></span>  
 <span data-ttu-id="3c189-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c189-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c189-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c189-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c189-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c189-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c189-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c189-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c189-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c189-113">See Also</span></span>  
 [<span data-ttu-id="3c189-114">Idebuggerthreadcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c189-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
