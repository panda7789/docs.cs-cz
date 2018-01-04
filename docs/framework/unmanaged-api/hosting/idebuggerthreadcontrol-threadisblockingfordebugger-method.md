---
title: "IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59a4c13e84414dcd10b217134334777a745431c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="73bd4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="73bd4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="73bd4-103">Upozorní hostitele, který podproces, který odesílá tento zpětné volání je o blok v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="73bd4-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73bd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73bd4-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="73bd4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73bd4-105">Remarks</span></span>  
 <span data-ttu-id="73bd4-106">`ThreadIsBlockingForDebugger` Metoda bude volána vždy v podprocesu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="73bd4-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="73bd4-107">`ThreadIsBlockingForDebugger` Metoda dává hostitele možnost provést další akci zablokuje přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="73bd4-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73bd4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73bd4-108">Requirements</span></span>  
 <span data-ttu-id="73bd4-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73bd4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73bd4-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73bd4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73bd4-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73bd4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73bd4-112">**NET Framework verze:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73bd4-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bd4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="73bd4-113">See Also</span></span>  
 [<span data-ttu-id="73bd4-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73bd4-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
