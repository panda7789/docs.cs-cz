---
title: "ICorPublishProcess::EnumAppDomains – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.EnumAppDomains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 09d6a75fa5c0562f466dba45707795ef7fd161db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="e448a-102">ICorPublishProcess::EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="e448a-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="e448a-103">Získá enumerátor pro aplikační domény v procesu, který je odkazován objektem to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e448a-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e448a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e448a-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e448a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e448a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e448a-106">[out] Ukazatel na adresu [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která umožňuje iteraci prostřednictvím kolekce aplikační domény v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="e448a-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e448a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e448a-107">Remarks</span></span>  
 <span data-ttu-id="e448a-108">Seznam domén aplikace je založena na snímek domény aplikace, které existují při `EnumAppDomains` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="e448a-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="e448a-109">Tato metoda může více než jednou volána k vytvoření nového seznamu aktuální.</span><span class="sxs-lookup"><span data-stu-id="e448a-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="e448a-110">Existující seznamy nebude mít vliv následující volání této metody.</span><span class="sxs-lookup"><span data-stu-id="e448a-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="e448a-111">Pokud proces byl ukončen, `EnumAppDomains` se nezdaří s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="e448a-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e448a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e448a-112">Requirements</span></span>  
 <span data-ttu-id="e448a-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e448a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e448a-114">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e448a-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e448a-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e448a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e448a-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e448a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e448a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e448a-117">See Also</span></span>  
 [<span data-ttu-id="e448a-118">ICorPublishProcess – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="e448a-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
