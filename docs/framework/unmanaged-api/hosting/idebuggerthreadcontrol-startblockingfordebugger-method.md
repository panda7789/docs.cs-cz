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
ms.openlocfilehash: 878dba37728734a777d2f95226b60bfbe9aae16a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805273"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="eaf28-102">IDebuggerThreadControl::StartBlockingForDebugger – metoda</span><span class="sxs-lookup"><span data-stu-id="eaf28-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="eaf28-103">Upozorňuje hostitele, že se chystá služby ladění zahájit blokování všech vláken.</span><span class="sxs-lookup"><span data-stu-id="eaf28-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf28-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaf28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eaf28-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="eaf28-106">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="eaf28-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaf28-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eaf28-107">Remarks</span></span>  
 <span data-ttu-id="eaf28-108">`StartBlockingForDebugger`Metodu lze volat ve vlákně modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="eaf28-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaf28-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eaf28-109">Requirements</span></span>  
 <span data-ttu-id="eaf28-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eaf28-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaf28-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eaf28-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaf28-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="eaf28-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaf28-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaf28-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf28-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaf28-114">See also</span></span>

- [<span data-ttu-id="eaf28-115">IDebuggerThreadControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eaf28-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
