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
ms.openlocfilehash: 4799c1d04e8172c604eeec50f2b841a6db063949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790586"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="6d803-102">ICorPublishProcess::EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="6d803-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="6d803-103">Získá enumerátor pro domény aplikace v procesu, na který odkazuje tento [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="6d803-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d803-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d803-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d803-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d803-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6d803-106">mimo Ukazatel na adresu instance [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která umožňuje iteraci v kolekci aplikačních domén v tomto procesu.</span><span class="sxs-lookup"><span data-stu-id="6d803-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d803-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d803-107">Remarks</span></span>  
 <span data-ttu-id="6d803-108">Seznam domén aplikace je založen na snímku domén aplikace, které existují při volání metody `EnumAppDomains`.</span><span class="sxs-lookup"><span data-stu-id="6d803-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="6d803-109">Tato metoda může být volána více než jednou pro vytvoření nového seznamu v aktuálním stavu.</span><span class="sxs-lookup"><span data-stu-id="6d803-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="6d803-110">Existující seznamy nebudou ovlivněny následnými voláními této metody.</span><span class="sxs-lookup"><span data-stu-id="6d803-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="6d803-111">Pokud byl proces ukončen, `EnumAppDomains` se nezdaří s hodnotou HRESULT CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="6d803-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d803-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d803-112">Requirements</span></span>  
 <span data-ttu-id="6d803-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d803-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d803-114">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6d803-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6d803-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d803-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d803-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d803-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d803-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d803-117">See also</span></span>

- [<span data-ttu-id="6d803-118">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d803-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
