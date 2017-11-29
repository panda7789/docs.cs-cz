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
ms.openlocfilehash: 5b14818f06fec78cfc2cff9ea66548c9ee87bb4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="40bfb-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="40bfb-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="40bfb-103">Upozorní hostitele, který podproces, který odesílá tento zpětné volání je o blok v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="40bfb-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40bfb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40bfb-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="40bfb-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40bfb-105">Remarks</span></span>  
 <span data-ttu-id="40bfb-106">`ThreadIsBlockingForDebugger` Metoda bude volána vždy v podprocesu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="40bfb-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="40bfb-107">`ThreadIsBlockingForDebugger` Metoda dává hostitele možnost provést další akci zablokuje přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="40bfb-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40bfb-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40bfb-108">Requirements</span></span>  
 <span data-ttu-id="40bfb-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40bfb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40bfb-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40bfb-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40bfb-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40bfb-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40bfb-112">**NET Framework verze:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40bfb-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40bfb-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="40bfb-113">See Also</span></span>  
 [<span data-ttu-id="40bfb-114">Idebuggerthreadcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="40bfb-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
