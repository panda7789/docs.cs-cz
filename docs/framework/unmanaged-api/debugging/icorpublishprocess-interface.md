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
ms.openlocfilehash: 08dfa3ddbfd9cffdb0cb88d0325e5703a854668a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182959"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="64787-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64787-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="64787-103">Poskytuje metody, které přistupují k zobrazit informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="64787-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64787-104">Metody</span><span class="sxs-lookup"><span data-stu-id="64787-104">Methods</span></span>  
  
|<span data-ttu-id="64787-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="64787-105">Method</span></span>|<span data-ttu-id="64787-106">Popis</span><span class="sxs-lookup"><span data-stu-id="64787-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64787-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="64787-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="64787-108">Získá [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance, která obsahuje domény aplikace v procesu odkazovaná tímto objektem `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="64787-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="64787-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="64787-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="64787-110">Získá úplnou cestu ke spustitelnému souboru pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="64787-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="64787-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="64787-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="64787-112">Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="64787-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="64787-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="64787-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="64787-114">Získá hodnotu určující, zda proces odkazuje toto `ICorPublishProcess` známé spouštět spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="64787-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64787-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64787-115">Requirements</span></span>  
 <span data-ttu-id="64787-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64787-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64787-117">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="64787-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="64787-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64787-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="64787-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="64787-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64787-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64787-120">See also</span></span>

- [<span data-ttu-id="64787-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64787-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="64787-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="64787-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
