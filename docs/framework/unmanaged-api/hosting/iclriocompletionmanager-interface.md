---
title: ICLRIoCompletionManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141031"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="9fed5-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fed5-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="9fed5-103">Implementuje metodu zpětného volání, která umožňuje hostiteli upozorňovat modul CLR (Common Language Runtime) na stav zadaných vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="9fed5-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fed5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9fed5-104">Methods</span></span>  
  
|<span data-ttu-id="9fed5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9fed5-105">Method</span></span>|<span data-ttu-id="9fed5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9fed5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fed5-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="9fed5-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="9fed5-108">Upozorňuje CLR na stav vstupně-výstupní žádosti, která byla vytvořena pomocí volání metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9fed5-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fed5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fed5-109">Remarks</span></span>  
 <span data-ttu-id="9fed5-110">Hostitel implementuje abstrakci dokončení vstupně-výstupních operací pomocí rozhraní [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9fed5-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="9fed5-111">Modul CLR vytvoří v rámci tohoto rozhraní vstupně-výstupní požadavky a hostitel upozorní modul runtime výsledku takových požadavků pomocí rozhraní `ICLRIoCompletionManager`.</span><span class="sxs-lookup"><span data-stu-id="9fed5-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fed5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fed5-112">Requirements</span></span>  
 <span data-ttu-id="9fed5-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fed5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fed5-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9fed5-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fed5-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9fed5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fed5-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fed5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fed5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fed5-117">See also</span></span>

- [<span data-ttu-id="9fed5-118">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fed5-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="9fed5-119">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fed5-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="9fed5-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9fed5-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
