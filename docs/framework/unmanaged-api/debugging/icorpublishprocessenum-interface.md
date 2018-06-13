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
ms.openlocfilehash: dd71a2bd4a52da8fa77592363e2eb7c8f5101fd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423982"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="15a30-102">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="15a30-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="15a30-103">Podtřídou třídy [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) rozhraní, které poskytuje metody k procházení kolekce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objekty.</span><span class="sxs-lookup"><span data-stu-id="15a30-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15a30-104">Metody</span><span class="sxs-lookup"><span data-stu-id="15a30-104">Methods</span></span>  
  
|<span data-ttu-id="15a30-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="15a30-105">Method</span></span>|<span data-ttu-id="15a30-106">Popis</span><span class="sxs-lookup"><span data-stu-id="15a30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15a30-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="15a30-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="15a30-108">Získá zadaný počet `ICorPublishProcess` instancí z kolekce, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="15a30-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15a30-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15a30-109">Remarks</span></span>  
 <span data-ttu-id="15a30-110">`ICorPublishProcessEnum` Rozhraní implementuje metody rozhraní abstraktní [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="15a30-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="15a30-111">`ICorPublishProcessEnum` Je instance vytvořené [icorpublish::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="15a30-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="15a30-112">Přechod kolekce `ICorPublishProcess` objekty podle kritéria filtru, která je zadána v době `ICorPublishProcessEnum` instance byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="15a30-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a30-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="15a30-113">Requirements</span></span>  
 <span data-ttu-id="15a30-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a30-115">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="15a30-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="15a30-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15a30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15a30-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a30-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="15a30-118">See Also</span></span>  
 [<span data-ttu-id="15a30-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="15a30-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="15a30-120">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="15a30-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
