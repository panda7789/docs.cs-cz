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
ms.openlocfilehash: 3ae48df9e66890161c1aef944d37b0a279939d56
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790545"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="19d70-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19d70-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="19d70-103">Poskytuje metody, které mají přístup k informacím, které se mají zobrazit o procesu.</span><span class="sxs-lookup"><span data-stu-id="19d70-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19d70-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19d70-104">Methods</span></span>  
  
|<span data-ttu-id="19d70-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19d70-105">Method</span></span>|<span data-ttu-id="19d70-106">Popis</span><span class="sxs-lookup"><span data-stu-id="19d70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19d70-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="19d70-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="19d70-108">Získá instanci [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která obsahuje domény aplikace v procesu, na který odkazuje tento `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="19d70-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19d70-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="19d70-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="19d70-110">Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje tento `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="19d70-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19d70-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="19d70-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="19d70-112">Získá identifikátor operačního systému pro proces, na který odkazuje tento `ICorPublishProcess`.</span><span class="sxs-lookup"><span data-stu-id="19d70-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="19d70-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="19d70-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="19d70-114">Získá hodnotu, která označuje, zda je v procesu odkazovaném tímto `ICorPublishProcess` spuštěn spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="19d70-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19d70-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19d70-115">Requirements</span></span>  
 <span data-ttu-id="19d70-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d70-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d70-117">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="19d70-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="19d70-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19d70-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19d70-119">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19d70-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d70-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19d70-120">See also</span></span>

- [<span data-ttu-id="19d70-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19d70-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="19d70-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="19d70-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
