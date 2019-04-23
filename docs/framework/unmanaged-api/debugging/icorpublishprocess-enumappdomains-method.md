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
ms.openlocfilehash: 173a7d6793bec9262efb661d56e3a371d0bf9b47
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164603"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="9d6de-102">ICorPublishProcess::EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="9d6de-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="9d6de-103">Získá enumerátor pro domény aplikace v procesu, který se odkazuje v tomto [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9d6de-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6de-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6de-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9d6de-106">[out] Ukazatel na adresu [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která umožňuje iteraci prostřednictvím kolekce aplikační domény v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="9d6de-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d6de-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d6de-107">Remarks</span></span>  
 <span data-ttu-id="9d6de-108">Seznam domén aplikace je založena na snímek domény aplikace, které existují při `EnumAppDomains` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="9d6de-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="9d6de-109">Tato metoda může být volána více než jednou. Chcete-li vytvořit nový seznam aktuální.</span><span class="sxs-lookup"><span data-stu-id="9d6de-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="9d6de-110">Existující seznamy tyto zásady neovlivní z následných volání této metody.</span><span class="sxs-lookup"><span data-stu-id="9d6de-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="9d6de-111">Pokud proces byl ukončen, `EnumAppDomains` dojde k selhání s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="9d6de-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6de-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d6de-112">Requirements</span></span>  
 <span data-ttu-id="9d6de-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6de-114">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9d6de-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9d6de-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d6de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d6de-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6de-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d6de-117">See also</span></span>

- [<span data-ttu-id="9d6de-118">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d6de-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
