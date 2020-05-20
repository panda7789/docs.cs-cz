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
ms.openlocfilehash: 657d2d638a419ba88d4cf7152f4505de1bd23706
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421069"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="c64f3-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c64f3-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="c64f3-103">Podtřída rozhraní [ICorPublishEnum](icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c64f3-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c64f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c64f3-104">Methods</span></span>  
  
|<span data-ttu-id="c64f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c64f3-105">Method</span></span>|<span data-ttu-id="c64f3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c64f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c64f3-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c64f3-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="c64f3-108">Načte zadaný počet `ICorPublishProcess` instancí z kolekce počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="c64f3-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c64f3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c64f3-109">Remarks</span></span>  
 <span data-ttu-id="c64f3-110">`ICorPublishProcessEnum`Rozhraní implementuje metody abstraktního rozhraní [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c64f3-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="c64f3-111">`ICorPublishProcessEnum`Instance je vytvořena metodou [ICorPublish –:: EnumProcesses –](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c64f3-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="c64f3-112">Průchod kolekce `ICorPublishProcess` objektů je založen na kritériích filtru uvedených v době, kdy `ICorPublishProcessEnum` byla vytvořena instance.</span><span class="sxs-lookup"><span data-stu-id="c64f3-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c64f3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c64f3-113">Requirements</span></span>  
 <span data-ttu-id="c64f3-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c64f3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c64f3-115">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c64f3-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c64f3-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c64f3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c64f3-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c64f3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c64f3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c64f3-118">See also</span></span>

- [<span data-ttu-id="c64f3-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c64f3-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c64f3-120">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="c64f3-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
