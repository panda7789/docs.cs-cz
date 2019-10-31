---
title: ICorPublishProcessEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103421"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="99595-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99595-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="99595-103">Podtřída rozhraní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="99595-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99595-104">Metody</span><span class="sxs-lookup"><span data-stu-id="99595-104">Methods</span></span>  
  
|<span data-ttu-id="99595-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="99595-105">Method</span></span>|<span data-ttu-id="99595-106">Popis</span><span class="sxs-lookup"><span data-stu-id="99595-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99595-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="99595-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="99595-108">Získá zadaný počet instancí `ICorPublishProcess` z kolekce počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="99595-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99595-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99595-109">Remarks</span></span>  
 <span data-ttu-id="99595-110">Rozhraní `ICorPublishProcessEnum` implementuje metody abstraktního rozhraní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="99595-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="99595-111">Instance `ICorPublishProcessEnum` je vytvořena metodou [ICorPublish –:: EnumProcesses –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99595-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="99595-112">Průchod kolekce `ICorPublishProcess` objektů je založen na kritériích filtru uvedených v době, kdy byla vytvořena instance `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="99595-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99595-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99595-113">Requirements</span></span>  
 <span data-ttu-id="99595-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99595-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99595-115">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="99595-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="99595-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99595-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99595-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99595-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99595-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99595-118">See also</span></span>

- [<span data-ttu-id="99595-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="99595-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="99595-120">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="99595-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
