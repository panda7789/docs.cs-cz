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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7864bb81c3b457bf8ec07cd194d24b29a42bd441
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767465"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="52de8-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52de8-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="52de8-103">Implementuje metodu zpětného volání, která umožňuje hostitele tak, aby upozornění common language runtime (CLR) stavu zadaného vstupně-výstupní požadavky.</span><span class="sxs-lookup"><span data-stu-id="52de8-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52de8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="52de8-104">Methods</span></span>  
  
|<span data-ttu-id="52de8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="52de8-105">Method</span></span>|<span data-ttu-id="52de8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="52de8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52de8-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="52de8-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="52de8-108">Upozorní CLR stav požadavku vstupně-výstupní operace, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="52de8-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52de8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52de8-109">Remarks</span></span>  
 <span data-ttu-id="52de8-110">Hostitel implementuje pomocí abstrakce dokončení vstupně-výstupních operací [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52de8-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="52de8-111">Modul CLR provede vstupně-výstupní požadavky prostřednictvím tohoto rozhraní a hostitele upozorní runtime výsledky těchto požadavků pomocí `ICLRIoCompletionManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="52de8-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52de8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52de8-112">Requirements</span></span>  
 <span data-ttu-id="52de8-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52de8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52de8-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="52de8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52de8-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52de8-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52de8-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52de8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52de8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52de8-117">See also</span></span>

- [<span data-ttu-id="52de8-118">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52de8-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="52de8-119">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52de8-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="52de8-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="52de8-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
