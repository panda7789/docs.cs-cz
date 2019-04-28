---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ff178cc9ab798593848e56fc7bba8ac82ae295
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699692"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="7b805-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="7b805-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="7b805-103">Upozorňuje hostitele, který spočívá v vlákna, která se odesílá toto zpětné volání do bloku v rámci služeb ladění.</span><span class="sxs-lookup"><span data-stu-id="7b805-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b805-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b805-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b805-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b805-105">Remarks</span></span>  
 <span data-ttu-id="7b805-106">`ThreadIsBlockingForDebugger` Metoda bude volána vždy ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7b805-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="7b805-107">`ThreadIsBlockingForDebugger` Metoda poskytuje hostiteli příležitost provést jinou akci při vlákno blokováno.</span><span class="sxs-lookup"><span data-stu-id="7b805-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b805-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b805-108">Requirements</span></span>  
 <span data-ttu-id="7b805-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b805-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b805-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7b805-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b805-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b805-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b805-112">**Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b805-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b805-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b805-113">See also</span></span>

- [<span data-ttu-id="7b805-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b805-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
