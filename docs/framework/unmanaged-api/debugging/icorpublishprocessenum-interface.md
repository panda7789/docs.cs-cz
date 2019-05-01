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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993475"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="79427-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79427-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="79427-103">Podtřída [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody, které procházejí kolekci [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="79427-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79427-104">Metody</span><span class="sxs-lookup"><span data-stu-id="79427-104">Methods</span></span>  
  
|<span data-ttu-id="79427-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="79427-105">Method</span></span>|<span data-ttu-id="79427-106">Popis</span><span class="sxs-lookup"><span data-stu-id="79427-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79427-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="79427-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="79427-108">Získá zadaný počet `ICorPublishProcess` instancí z kolekce, spouští se na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="79427-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79427-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79427-109">Remarks</span></span>  
 <span data-ttu-id="79427-110">`ICorPublishProcessEnum` Rozhraní implementuje metodu rozhraní abstraktní [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="79427-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="79427-111">`ICorPublishProcessEnum` Vytvoří instanci [icorpublish::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="79427-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="79427-112">Procházení kolekce `ICorPublishProcess` objekty je založená na filtru kritérií uvedených v době `ICorPublishProcessEnum` instance byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="79427-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79427-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79427-113">Requirements</span></span>  
 <span data-ttu-id="79427-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79427-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79427-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="79427-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="79427-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79427-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79427-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79427-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79427-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79427-118">See also</span></span>

- [<span data-ttu-id="79427-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="79427-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="79427-120">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="79427-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
