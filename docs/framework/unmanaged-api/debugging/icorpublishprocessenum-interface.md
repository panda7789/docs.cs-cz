---
title: "ICorPublishProcessEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcessEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcessEnum
helpviewer_keywords: ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 66e31911289d1ef8b590a0b7e7896adfa4998adc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="3b0e7-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b0e7-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="3b0e7-103">Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b0e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3b0e7-104">Methods</span></span>  
  
|<span data-ttu-id="3b0e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3b0e7-105">Method</span></span>|<span data-ttu-id="3b0e7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3b0e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b0e7-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="3b0e7-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="3b0e7-108">Získá zadaný počet `ICorPublishProcess` instancí z kolekce, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b0e7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b0e7-109">Remarks</span></span>  
 <span data-ttu-id="3b0e7-110">`ICorPublishProcessEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="3b0e7-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="3b0e7-111">`ICorPublishProcessEnum` Je instance vytvořené [icorpublish::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="3b0e7-112">Přechod kolekce `ICorPublishProcess` objekty podle kritéria filtru, která je zadána v době `ICorPublishProcessEnum` instance byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="3b0e7-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b0e7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b0e7-113">Requirements</span></span>  
 <span data-ttu-id="3b0e7-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b0e7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b0e7-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3b0e7-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3b0e7-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b0e7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b0e7-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b0e7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0e7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b0e7-118">See Also</span></span>  
 [<span data-ttu-id="3b0e7-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="3b0e7-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3b0e7-120">Corpubpublish – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="3b0e7-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
