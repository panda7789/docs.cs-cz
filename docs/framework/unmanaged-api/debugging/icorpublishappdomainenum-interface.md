---
title: "ICorPublishAppDomainEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum
helpviewer_keywords: ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8359eda5432a9b3818fd58f6adc18570e4c5f154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="7ed42-102">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ed42-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="7ed42-103">Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objekty, které aktuálně existovat v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7ed42-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ed42-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ed42-104">Methods</span></span>  
  
|<span data-ttu-id="7ed42-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ed42-105">Method</span></span>|<span data-ttu-id="7ed42-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7ed42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ed42-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7ed42-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="7ed42-108">Získá zadaný počet `ICorPublishAppDomain` instancí z kolekce, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="7ed42-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ed42-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ed42-109">Remarks</span></span>  
 <span data-ttu-id="7ed42-110">`ICorPublishAppDomainEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7ed42-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ed42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ed42-111">Requirements</span></span>  
 <span data-ttu-id="7ed42-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ed42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ed42-113">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7ed42-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7ed42-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ed42-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ed42-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ed42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed42-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ed42-116">See Also</span></span>  
 [<span data-ttu-id="7ed42-117">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7ed42-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7ed42-118">Corpubpublish – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="7ed42-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
