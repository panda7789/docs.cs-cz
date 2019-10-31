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
ms.openlocfilehash: 067d4e844055206543e5c7fb409296b0d0a7a549
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134943"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="49bb4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="49bb4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="49bb4-103">Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="49bb4-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49bb4-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="49bb4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49bb4-105">Remarks</span></span>  
 <span data-ttu-id="49bb4-106">Metoda `ThreadIsBlockingForDebugger` bude vždy volána ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="49bb4-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="49bb4-107">Metoda `ThreadIsBlockingForDebugger` dává hostiteli možnost provést další akci během bloků vlákna.</span><span class="sxs-lookup"><span data-stu-id="49bb4-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49bb4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49bb4-108">Requirements</span></span>  
 <span data-ttu-id="49bb4-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49bb4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49bb4-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49bb4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49bb4-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49bb4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49bb4-112">**Verze rozhraní .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49bb4-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bb4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49bb4-113">See also</span></span>

- [<span data-ttu-id="49bb4-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49bb4-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
