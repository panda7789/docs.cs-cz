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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09895294c4678cdb1dd033076cfb42853aa06b2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780503"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="42c21-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="42c21-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="42c21-103">Upozorňuje hostitele, že ladění služby se chystáte uvolnit všechna vlákna, které jsou blokovány.</span><span class="sxs-lookup"><span data-stu-id="42c21-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c21-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="42c21-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42c21-105">Remarks</span></span>  
 <span data-ttu-id="42c21-106">`ReleaseAllRuntimeThreads` Ve vlákně modulu runtime nebude nikdy volána metoda.</span><span class="sxs-lookup"><span data-stu-id="42c21-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="42c21-107">Pokud má hostitel modulu runtime vlákno blokované, to by měla uvolnit ji nyní.</span><span class="sxs-lookup"><span data-stu-id="42c21-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c21-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42c21-108">Requirements</span></span>  
 <span data-ttu-id="42c21-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c21-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c21-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42c21-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42c21-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42c21-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42c21-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c21-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c21-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42c21-113">See also</span></span>

- [<span data-ttu-id="42c21-114">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42c21-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
