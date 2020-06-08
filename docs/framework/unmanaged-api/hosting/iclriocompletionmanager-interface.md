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
ms.openlocfilehash: 71afc5e9772f82b922e8f428e6d808e46d092704
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504209"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="bf05c-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf05c-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="bf05c-103">Implementuje metodu zpětného volání, která umožňuje hostiteli upozorňovat modul CLR (Common Language Runtime) na stav zadaných vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="bf05c-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf05c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bf05c-104">Methods</span></span>  
  
|<span data-ttu-id="bf05c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf05c-105">Method</span></span>|<span data-ttu-id="bf05c-106">Description</span><span class="sxs-lookup"><span data-stu-id="bf05c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf05c-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="bf05c-107">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="bf05c-108">Upozorňuje CLR na stav vstupně-výstupní žádosti, která byla vytvořena pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bf05c-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf05c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf05c-109">Remarks</span></span>  
 <span data-ttu-id="bf05c-110">Hostitel implementuje abstrakci dokončení vstupně-výstupních operací pomocí rozhraní [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bf05c-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="bf05c-111">CLR vytvoří v/v požadavky prostřednictvím tohoto rozhraní a hostitel upozorní modul runtime na výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bf05c-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf05c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf05c-112">Requirements</span></span>  
 <span data-ttu-id="bf05c-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf05c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf05c-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bf05c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf05c-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf05c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf05c-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf05c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf05c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf05c-117">See also</span></span>

- [<span data-ttu-id="bf05c-118">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf05c-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="bf05c-119">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf05c-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="bf05c-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="bf05c-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
