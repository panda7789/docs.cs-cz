---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 9ae1aa6590366468166916e6a92d0b356eb37c27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133144"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="9fe54-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="9fe54-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="9fe54-103">Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.</span><span class="sxs-lookup"><span data-stu-id="9fe54-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fe54-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="9fe54-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fe54-105">Remarks</span></span>  
 <span data-ttu-id="9fe54-106">Metoda `ReleaseAllRuntimeThreads` nebude nikdy volána ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9fe54-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="9fe54-107">Pokud má hostitel běhové vlákno, je třeba ho uvolnit hned.</span><span class="sxs-lookup"><span data-stu-id="9fe54-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe54-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fe54-108">Requirements</span></span>  
 <span data-ttu-id="9fe54-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fe54-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe54-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9fe54-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fe54-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9fe54-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fe54-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fe54-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe54-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fe54-113">See also</span></span>

- [<span data-ttu-id="9fe54-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fe54-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
