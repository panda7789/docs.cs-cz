---
title: IDebuggerThreadControl::StartBlockingForDebugger – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cb314f2afce0cbbf1c5fb185f516a30ad8313af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780509"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="a975d-102">IDebuggerThreadControl::StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="a975d-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="a975d-103">Upozorňuje hostitele, spustí blokující všechna vlákna jsou ladění služby.</span><span class="sxs-lookup"><span data-stu-id="a975d-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a975d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a975d-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a975d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a975d-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="a975d-106">[in] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="a975d-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a975d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a975d-107">Remarks</span></span>  
 <span data-ttu-id="a975d-108">`StartBlockingForDebugger` Metoda může být volána ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a975d-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a975d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a975d-109">Requirements</span></span>  
 <span data-ttu-id="a975d-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a975d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a975d-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a975d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a975d-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a975d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a975d-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a975d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a975d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a975d-114">See also</span></span>

- [<span data-ttu-id="a975d-115">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a975d-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
