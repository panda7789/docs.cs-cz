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
ms.openlocfilehash: 610f62274aea88c1d5f9bbe1456685aa1d3bca68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423738"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="7c451-102">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c451-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="7c451-103">Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objekty, které aktuálně existovat v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7c451-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c451-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c451-104">Methods</span></span>  
  
|<span data-ttu-id="7c451-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c451-105">Method</span></span>|<span data-ttu-id="7c451-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7c451-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c451-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7c451-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="7c451-108">Získá zadaný počet `ICorPublishAppDomain` instancí z kolekce, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="7c451-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c451-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c451-109">Remarks</span></span>  
 <span data-ttu-id="7c451-110">`ICorPublishAppDomainEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7c451-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c451-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c451-111">Requirements</span></span>  
 <span data-ttu-id="7c451-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c451-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c451-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7c451-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7c451-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c451-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c451-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c451-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c451-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c451-116">See Also</span></span>  
 [<span data-ttu-id="7c451-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7c451-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7c451-118">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="7c451-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
