---
title: "ICorPublishEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7034945824e439b42134f8ea3c13bfaf73dbb649
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="11a6a-102">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11a6a-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="11a6a-103">Slouží jako abstraktní základní rozhraní pro výčty, které se používají v publikování informací o procesy a aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="11a6a-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11a6a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="11a6a-104">Methods</span></span>  
  
|<span data-ttu-id="11a6a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="11a6a-105">Method</span></span>|<span data-ttu-id="11a6a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="11a6a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11a6a-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="11a6a-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="11a6a-108">Vytvoří kopii tohoto `ICorPublishEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="11a6a-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="11a6a-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="11a6a-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="11a6a-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="11a6a-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="11a6a-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="11a6a-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="11a6a-112">Posune kurzor z na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="11a6a-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="11a6a-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="11a6a-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="11a6a-114">Přesune kurzor dál o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="11a6a-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11a6a-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11a6a-115">Remarks</span></span>  
 <span data-ttu-id="11a6a-116">Následující výčty odvozena od `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="11a6a-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="11a6a-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="11a6a-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="11a6a-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="11a6a-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="11a6a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11a6a-119">Requirements</span></span>  
 <span data-ttu-id="11a6a-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a6a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a6a-121">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="11a6a-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="11a6a-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11a6a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11a6a-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a6a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a6a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="11a6a-124">See Also</span></span>  
 [<span data-ttu-id="11a6a-125">Corpubpublish – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="11a6a-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="11a6a-126">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="11a6a-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
