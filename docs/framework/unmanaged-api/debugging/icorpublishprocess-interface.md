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
ms.openlocfilehash: 19f76a163fae4a1390a2e0fcb85299f8ce78180c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435887"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="ae5d5-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae5d5-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="ae5d5-103">Poskytuje metody, která přistupují k zobrazit informace o procesu.</span><span class="sxs-lookup"><span data-stu-id="ae5d5-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae5d5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae5d5-104">Methods</span></span>  
  
|<span data-ttu-id="ae5d5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae5d5-105">Method</span></span>|<span data-ttu-id="ae5d5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ae5d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae5d5-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="ae5d5-107">EnumAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="ae5d5-108">Získá [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instanci, která obsahuje aplikační domény v procesu odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="ae5d5-108">Gets an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5d5-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="ae5d5-109">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="ae5d5-110">Získá úplnou cestu ke spustitelnému souboru procesu, který odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="ae5d5-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5d5-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="ae5d5-111">GetProcessID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="ae5d5-112">Získá identifikátor operačního systému pro proces odkazuje toto `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="ae5d5-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="ae5d5-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="ae5d5-113">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="ae5d5-114">Získá hodnotu, která určuje, jestli proces odkazuje toto `ICorPublishProcess` je známé, aby byl spuštěn spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ae5d5-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae5d5-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae5d5-115">Requirements</span></span>  
 <span data-ttu-id="ae5d5-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae5d5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5d5-117">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ae5d5-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ae5d5-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae5d5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae5d5-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5d5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5d5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae5d5-120">See Also</span></span>  
 [<span data-ttu-id="ae5d5-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ae5d5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ae5d5-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="ae5d5-122">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
