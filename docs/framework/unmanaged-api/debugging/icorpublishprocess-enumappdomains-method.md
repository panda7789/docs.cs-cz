---
title: ICorPublishProcess::EnumAppDomains – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5492d4e1245c6c0ce5c1eb98d25168c5d69d123b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423699"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="48cb6-102">ICorPublishProcess::EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="48cb6-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="48cb6-103">Získá enumerátor pro aplikační domény v procesu, který je odkazován objektem to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="48cb6-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48cb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48cb6-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48cb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48cb6-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="48cb6-106">[out] Ukazatel na adresu [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která umožňuje iteraci prostřednictvím kolekce aplikační domény v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="48cb6-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48cb6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48cb6-107">Remarks</span></span>  
 <span data-ttu-id="48cb6-108">Seznam domén aplikace je založena na snímek domény aplikace, které existují při `EnumAppDomains` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="48cb6-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="48cb6-109">Tato metoda může více než jednou volána k vytvoření nového seznamu aktuální.</span><span class="sxs-lookup"><span data-stu-id="48cb6-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="48cb6-110">Existující seznamy nebude mít vliv následující volání této metody.</span><span class="sxs-lookup"><span data-stu-id="48cb6-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="48cb6-111">Pokud proces byl ukončen, `EnumAppDomains` se nezdaří s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="48cb6-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48cb6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48cb6-112">Requirements</span></span>  
 <span data-ttu-id="48cb6-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48cb6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48cb6-114">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="48cb6-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="48cb6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48cb6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48cb6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48cb6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48cb6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="48cb6-117">See Also</span></span>  
 [<span data-ttu-id="48cb6-118">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48cb6-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
