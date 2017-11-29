---
title: "ICorPublishProcess – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess
helpviewer_keywords: ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cb62da277ff13bea33969bb9c728cac5d5a15554
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="894b7-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="894b7-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="894b7-103">Poskytuje metody, která přistupují k zobrazit informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="894b7-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="894b7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="894b7-104">Methods</span></span>  
  
|<span data-ttu-id="894b7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="894b7-105">Method</span></span>|<span data-ttu-id="894b7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="894b7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="894b7-107">Enumappdomains – metoda</span><span class="sxs-lookup"><span data-stu-id="894b7-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="894b7-108">Získá [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která obsahuje aplikační domény v procesu odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="894b7-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="894b7-109">Getdisplayname – metoda</span><span class="sxs-lookup"><span data-stu-id="894b7-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="894b7-110">Získá úplnou cestu ke spustitelnému souboru procesu, který odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="894b7-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="894b7-111">Getprocessid – metoda</span><span class="sxs-lookup"><span data-stu-id="894b7-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="894b7-112">Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="894b7-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="894b7-113">Ismanaged – metoda</span><span class="sxs-lookup"><span data-stu-id="894b7-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="894b7-114">Získá hodnotu, která určuje, jestli proces odkazuje toto `ICorPublishProcess` je známé, aby byl spuštěn spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="894b7-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="894b7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="894b7-115">Requirements</span></span>  
 <span data-ttu-id="894b7-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="894b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="894b7-117">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="894b7-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="894b7-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="894b7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="894b7-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="894b7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894b7-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="894b7-120">See Also</span></span>  
 [<span data-ttu-id="894b7-121">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="894b7-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="894b7-122">Corpubpublish – třída typu Coclass</span><span class="sxs-lookup"><span data-stu-id="894b7-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
