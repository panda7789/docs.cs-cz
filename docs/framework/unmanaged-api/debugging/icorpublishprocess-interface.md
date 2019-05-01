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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993509"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="e60f6-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e60f6-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="e60f6-103">Poskytuje metody, které přistupují k zobrazit informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="e60f6-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e60f6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e60f6-104">Methods</span></span>  
  
|<span data-ttu-id="e60f6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e60f6-105">Method</span></span>|<span data-ttu-id="e60f6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e60f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e60f6-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="e60f6-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="e60f6-108">Získá [icorpublishappdomainenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance, která obsahuje domény aplikace v procesu odkazovaná tímto objektem `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e60f6-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e60f6-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="e60f6-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="e60f6-110">Získá úplnou cestu ke spustitelnému souboru pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e60f6-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e60f6-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="e60f6-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="e60f6-112">Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="e60f6-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="e60f6-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="e60f6-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="e60f6-114">Získá hodnotu určující, zda proces odkazuje toto `ICorPublishProcess` známé spouštět spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e60f6-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e60f6-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e60f6-115">Requirements</span></span>  
 <span data-ttu-id="e60f6-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e60f6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e60f6-117">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e60f6-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e60f6-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e60f6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e60f6-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e60f6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60f6-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e60f6-120">See also</span></span>

- [<span data-ttu-id="e60f6-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e60f6-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e60f6-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="e60f6-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
