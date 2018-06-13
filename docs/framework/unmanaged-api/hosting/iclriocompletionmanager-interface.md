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
ms.openlocfilehash: c3abb3e80226da909a0c7eb8e4bf54959557dcbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436264"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="da38a-102">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da38a-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="da38a-103">Implementuje požadavků metoda zpětného volání, která umožňuje hostiteli upozornit modul CLR (CLR) stavu zadaný vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="da38a-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da38a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="da38a-104">Methods</span></span>  
  
|<span data-ttu-id="da38a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="da38a-105">Method</span></span>|<span data-ttu-id="da38a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="da38a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da38a-107">OnComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="da38a-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="da38a-108">Upozorní CLR stavu požadavek vstupně-výstupních operací, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="da38a-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da38a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da38a-109">Remarks</span></span>  
 <span data-ttu-id="da38a-110">Hostitel implementuje abstraktní dokončení vstupně-výstupních operací pomocí [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="da38a-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="da38a-111">Modul CLR zadává vstupně-výstupních požadavků prostřednictvím tohoto rozhraní a hostitele upozorní modul runtime výsledek takových požadavků pomocí `ICLRIoCompletionManager` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="da38a-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da38a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da38a-112">Requirements</span></span>  
 <span data-ttu-id="da38a-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da38a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da38a-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da38a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da38a-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da38a-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da38a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da38a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da38a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="da38a-117">See Also</span></span>  
 [<span data-ttu-id="da38a-118">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da38a-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="da38a-119">IHostThreadPoolManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da38a-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="da38a-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="da38a-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
