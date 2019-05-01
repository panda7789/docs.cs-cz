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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993535"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="239e0-102">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="239e0-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="239e0-103">Slouží jako abstraktní základní rozhraní pro enumerátory, které se používají v publikování informací o procesy a aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="239e0-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="239e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="239e0-104">Methods</span></span>  
  
|<span data-ttu-id="239e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="239e0-105">Method</span></span>|<span data-ttu-id="239e0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="239e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="239e0-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="239e0-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="239e0-108">Vytvoří kopii tohoto `ICorPublishEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="239e0-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="239e0-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="239e0-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="239e0-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="239e0-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="239e0-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="239e0-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="239e0-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="239e0-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="239e0-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="239e0-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="239e0-114">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="239e0-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="239e0-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="239e0-115">Remarks</span></span>  
 <span data-ttu-id="239e0-116">Následující výčty jsou odvozeny z `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="239e0-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="239e0-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="239e0-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="239e0-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="239e0-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="239e0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="239e0-119">Requirements</span></span>  
 <span data-ttu-id="239e0-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="239e0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="239e0-121">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="239e0-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="239e0-122">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="239e0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="239e0-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="239e0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239e0-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="239e0-124">See also</span></span>

- [<span data-ttu-id="239e0-125">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="239e0-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="239e0-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="239e0-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
