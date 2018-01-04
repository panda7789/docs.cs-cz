---
title: "IDebuggerThreadControl::StartBlockingForDebugger – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.StartBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99c0bc78705fa07883d92bf0cc1d90300c5ac549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="c648d-102">IDebuggerThreadControl::StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="c648d-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="c648d-103">Upozorní hostitele, že ladění služby se chystáte se spustit blokování všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="c648d-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c648d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c648d-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c648d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c648d-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="c648d-106">[v] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="c648d-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c648d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c648d-107">Remarks</span></span>  
 <span data-ttu-id="c648d-108">`StartBlockingForDebugger` Metoda může být volána v podprocesu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c648d-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c648d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c648d-109">Requirements</span></span>  
 <span data-ttu-id="c648d-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c648d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c648d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c648d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c648d-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c648d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c648d-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c648d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c648d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c648d-114">See Also</span></span>  
 [<span data-ttu-id="c648d-115">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c648d-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
