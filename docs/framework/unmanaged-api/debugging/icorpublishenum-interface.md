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
ms.openlocfilehash: 7d083655326333f18ee98f8e84fff2ed182dde6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103453"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="0e90f-102">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e90f-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="0e90f-103">Slouží jako abstraktní základní rozhraní pro enumerátory používané při publikování informací o procesech a doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e90f-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e90f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e90f-104">Methods</span></span>  
  
|<span data-ttu-id="0e90f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e90f-105">Method</span></span>|<span data-ttu-id="0e90f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0e90f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e90f-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="0e90f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="0e90f-108">Vytvoří kopii tohoto objektu `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="0e90f-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="0e90f-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="0e90f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="0e90f-110">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0e90f-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="0e90f-111">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="0e90f-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="0e90f-112">Přesune kurzor na začátek výčtu.</span><span class="sxs-lookup"><span data-stu-id="0e90f-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="0e90f-113">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0e90f-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="0e90f-114">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="0e90f-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e90f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e90f-115">Remarks</span></span>  
 <span data-ttu-id="0e90f-116">Následující enumerátory jsou odvozeny z `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="0e90f-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="0e90f-117">ICorPublishAppDomainEnum –</span><span class="sxs-lookup"><span data-stu-id="0e90f-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="0e90f-118">ICorPublishProcessEnum –</span><span class="sxs-lookup"><span data-stu-id="0e90f-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="0e90f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e90f-119">Requirements</span></span>  
 <span data-ttu-id="0e90f-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e90f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e90f-121">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="0e90f-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0e90f-122">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e90f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e90f-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e90f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e90f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e90f-124">See also</span></span>

- [<span data-ttu-id="0e90f-125">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="0e90f-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="0e90f-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0e90f-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
