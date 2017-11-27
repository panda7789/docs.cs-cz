---
title: "ICLRIoCompletionManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="02e5b-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02e5b-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="02e5b-103">Implementuje požadavků metoda zpětného volání, která umožňuje hostiteli upozornit modul CLR (CLR) stavu zadaný vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="02e5b-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02e5b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="02e5b-104">Methods</span></span>  
  
|<span data-ttu-id="02e5b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="02e5b-105">Method</span></span>|<span data-ttu-id="02e5b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="02e5b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02e5b-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="02e5b-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="02e5b-108">Upozorní CLR stavu požadavek vstupně-výstupních operací, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="02e5b-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02e5b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02e5b-109">Remarks</span></span>  
 <span data-ttu-id="02e5b-110">Hostitel implementuje abstraktní dokončení vstupně-výstupních operací pomocí [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02e5b-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="02e5b-111">Modul CLR zadává vstupně-výstupních požadavků prostřednictvím tohoto rozhraní a hostitele upozorní modul runtime výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02e5b-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e5b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02e5b-112">Requirements</span></span>  
 <span data-ttu-id="02e5b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02e5b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e5b-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02e5b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02e5b-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02e5b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02e5b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e5b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e5b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="02e5b-117">See Also</span></span>  
 [<span data-ttu-id="02e5b-118">Ihostiocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02e5b-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="02e5b-119">Ihostthreadpoolmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02e5b-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="02e5b-120">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="02e5b-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
