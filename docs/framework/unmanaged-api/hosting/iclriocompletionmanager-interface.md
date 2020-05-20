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
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703562"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="2f169-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f169-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="2f169-103">Implementuje metodu zpětného volání, která umožňuje hostiteli upozorňovat modul CLR (Common Language Runtime) na stav zadaných vstupně-výstupních požadavků.</span><span class="sxs-lookup"><span data-stu-id="2f169-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f169-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f169-104">Methods</span></span>  
  
|<span data-ttu-id="2f169-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f169-105">Method</span></span>|<span data-ttu-id="2f169-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2f169-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f169-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="2f169-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="2f169-108">Upozorňuje CLR na stav vstupně-výstupní žádosti, která byla vytvořena pomocí volání metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2f169-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f169-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2f169-109">Remarks</span></span>  
 <span data-ttu-id="2f169-110">Hostitel implementuje abstrakci dokončení vstupně-výstupních operací pomocí rozhraní [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2f169-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="2f169-111">CLR vytvoří v/v požadavky prostřednictvím tohoto rozhraní a hostitel upozorní modul runtime na výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2f169-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f169-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2f169-112">Requirements</span></span>  
 <span data-ttu-id="2f169-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f169-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f169-114">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f169-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f169-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2f169-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f169-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f169-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f169-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f169-117">See also</span></span>

- [<span data-ttu-id="2f169-118">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f169-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="2f169-119">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2f169-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="2f169-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2f169-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
