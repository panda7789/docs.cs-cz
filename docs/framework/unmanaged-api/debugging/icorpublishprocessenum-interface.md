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
ms.openlocfilehash: 188ff8feabd704d828256a09aca20f9db2227f2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790500"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="4d08e-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d08e-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="4d08e-103">Podtřída rozhraní [ICorPublishEnum](icorpublishenum-interface.md) , která poskytuje metody pro procházení kolekce objektů [ICorPublishProcess](icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4d08e-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d08e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d08e-104">Methods</span></span>  
  
|<span data-ttu-id="4d08e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d08e-105">Method</span></span>|<span data-ttu-id="4d08e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4d08e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d08e-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4d08e-107">Next Method</span></span>](icorpublishprocessenum-next-method.md)|<span data-ttu-id="4d08e-108">Získá zadaný počet instancí `ICorPublishProcess` z kolekce počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="4d08e-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d08e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d08e-109">Remarks</span></span>  
 <span data-ttu-id="4d08e-110">Rozhraní `ICorPublishProcessEnum` implementuje metody abstraktního rozhraní [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4d08e-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="4d08e-111">Instance `ICorPublishProcessEnum` je vytvořena metodou [ICorPublish –:: EnumProcesses –](icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d08e-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="4d08e-112">Průchod kolekce `ICorPublishProcess` objektů je založen na kritériích filtru uvedených v době, kdy byla vytvořena instance `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="4d08e-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d08e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d08e-113">Requirements</span></span>  
 <span data-ttu-id="4d08e-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d08e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d08e-115">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="4d08e-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4d08e-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d08e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d08e-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d08e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d08e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d08e-118">See also</span></span>

- [<span data-ttu-id="4d08e-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4d08e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4d08e-120">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="4d08e-120">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
