---
title: ICorPublishAppDomainEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090027"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="cb04d-102">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb04d-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="cb04d-103">Podtřída [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody, které procházejí kolekci [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objekty, které momentálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="cb04d-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb04d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cb04d-104">Methods</span></span>  
  
|<span data-ttu-id="cb04d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb04d-105">Method</span></span>|<span data-ttu-id="cb04d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cb04d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb04d-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="cb04d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="cb04d-108">Získá zadaný počet `ICorPublishAppDomain` instancí z kolekce, spouští se na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="cb04d-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb04d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb04d-109">Remarks</span></span>  
 <span data-ttu-id="cb04d-110">`ICorPublishAppDomainEnum` Rozhraní implementuje metodu rozhraní abstraktní [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cb04d-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb04d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb04d-111">Requirements</span></span>  
 <span data-ttu-id="cb04d-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb04d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb04d-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cb04d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cb04d-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb04d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cb04d-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cb04d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb04d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb04d-116">See also</span></span>

- [<span data-ttu-id="cb04d-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb04d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cb04d-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="cb04d-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
