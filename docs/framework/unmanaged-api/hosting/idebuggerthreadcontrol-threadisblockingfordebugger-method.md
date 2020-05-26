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
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805257"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="8212d-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="8212d-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="8212d-103">Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.</span><span class="sxs-lookup"><span data-stu-id="8212d-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8212d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8212d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="8212d-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8212d-105">Remarks</span></span>  
 <span data-ttu-id="8212d-106">`ThreadIsBlockingForDebugger`Metoda bude vždy volána ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="8212d-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="8212d-107">`ThreadIsBlockingForDebugger`Metoda dává hostiteli možnost provést další akci během bloků vlákna.</span><span class="sxs-lookup"><span data-stu-id="8212d-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8212d-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8212d-108">Requirements</span></span>  
 <span data-ttu-id="8212d-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8212d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8212d-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8212d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8212d-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8212d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8212d-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8212d-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8212d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8212d-113">See also</span></span>

- [<span data-ttu-id="8212d-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8212d-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
