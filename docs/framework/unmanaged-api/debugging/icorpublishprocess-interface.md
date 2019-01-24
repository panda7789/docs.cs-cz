---
title: ICorPublishProcess – rozhraní
ms.date: 03/30/2017
api_name:
- ICorPublishProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess
helpviewer_keywords:
- ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 6d1dc41b-8aa2-4889-bb00-1cbccc00c123
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19bd34f95e17094a89e4929a5b6ae936afe39885
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531912"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="5ab91-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5ab91-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="5ab91-103">Poskytuje metody, které přistupují k zobrazit informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="5ab91-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ab91-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5ab91-104">Methods</span></span>  
  
|<span data-ttu-id="5ab91-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-105">Method</span></span>|<span data-ttu-id="5ab91-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5ab91-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ab91-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="5ab91-108">Získá [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance, která obsahuje domény aplikace v procesu odkazovaná tímto objektem `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5ab91-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5ab91-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="5ab91-110">Získá úplnou cestu ke spustitelnému souboru pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5ab91-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5ab91-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="5ab91-112">Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="5ab91-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="5ab91-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="5ab91-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="5ab91-114">Získá hodnotu určující, zda proces odkazuje toto `ICorPublishProcess` známé spouštět spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5ab91-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5ab91-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5ab91-115">Requirements</span></span>  
 <span data-ttu-id="5ab91-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab91-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab91-117">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5ab91-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5ab91-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ab91-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ab91-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab91-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab91-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ab91-120">See also</span></span>
- [<span data-ttu-id="5ab91-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5ab91-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5ab91-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="5ab91-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
