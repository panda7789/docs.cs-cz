---
title: ICorPublishEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160131"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="0ab0c-102">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ab0c-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="0ab0c-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které se používají v publikování informací o procesy a aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="0ab0c-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ab0c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0ab0c-104">Methods</span></span>  
  
|<span data-ttu-id="0ab0c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ab0c-105">Method</span></span>|<span data-ttu-id="0ab0c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0ab0c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ab0c-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab0c-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="0ab0c-108">Vytvoří kopii tohoto `ICorPublishEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="0ab0c-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="0ab0c-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab0c-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="0ab0c-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0ab0c-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="0ab0c-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab0c-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="0ab0c-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="0ab0c-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="0ab0c-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0ab0c-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="0ab0c-114">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0ab0c-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ab0c-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ab0c-115">Remarks</span></span>  
 <span data-ttu-id="0ab0c-116">Následující výčty jsou odvozeny z `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="0ab0c-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="0ab0c-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="0ab0c-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="0ab0c-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="0ab0c-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="0ab0c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ab0c-119">Requirements</span></span>  
 <span data-ttu-id="0ab0c-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ab0c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ab0c-121">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0ab0c-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0ab0c-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ab0c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ab0c-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ab0c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ab0c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ab0c-124">See also</span></span>

- [<span data-ttu-id="0ab0c-125">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="0ab0c-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="0ab0c-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ab0c-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
