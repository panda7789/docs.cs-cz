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
ms.openlocfilehash: 8d958e949612b502ab218f5c6b75779174d34e19
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421082"
---
# <a name="icorpublishprocess-interface"></a><span data-ttu-id="b2db1-102">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2db1-102">ICorPublishProcess Interface</span></span>
<span data-ttu-id="b2db1-103">Poskytuje metody, které mají přístup k informacím, které se mají zobrazit o procesu.</span><span class="sxs-lookup"><span data-stu-id="b2db1-103">Provides methods that access information to be displayed about a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2db1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2db1-104">Methods</span></span>  
  
|<span data-ttu-id="b2db1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2db1-105">Method</span></span>|<span data-ttu-id="b2db1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b2db1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2db1-107">EnumAppDomains – metoda</span><span class="sxs-lookup"><span data-stu-id="b2db1-107">EnumAppDomains Method</span></span>](icorpublishprocess-enumappdomains-method.md)|<span data-ttu-id="b2db1-108">Získá instanci [ICorPublishAppDomainEnum –](icorpublishappdomainenum-interface.md) , která obsahuje domény aplikace v procesu, na který odkazuje `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="b2db1-108">Gets an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that contains the application domains in the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b2db1-109">GetDisplayName – metoda</span><span class="sxs-lookup"><span data-stu-id="b2db1-109">GetDisplayName Method</span></span>](icorpublishprocess-getdisplayname-method.md)|<span data-ttu-id="b2db1-110">Získá úplnou cestu ke spustitelnému souboru pro proces, na který odkazuje `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="b2db1-110">Gets the full path of the executable for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b2db1-111">GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="b2db1-111">GetProcessID Method</span></span>](icorpublishprocess-getprocessid-method.md)|<span data-ttu-id="b2db1-112">Načte identifikátor operačního systému pro proces, na který odkazuje tento `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="b2db1-112">Gets the operating system identifier for the process referenced by this `ICorPublishProcess`.</span></span>|  
|[<span data-ttu-id="b2db1-113">IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="b2db1-113">IsManaged Method</span></span>](icorpublishprocess-ismanaged-method.md)|<span data-ttu-id="b2db1-114">Získá hodnotu, která označuje, zda je známý proces, na který odkazuje tento `ICorPublishProcess` spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="b2db1-114">Gets a value that indicates whether the process referenced by this `ICorPublishProcess` is known to be running managed code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2db1-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2db1-115">Requirements</span></span>  
 <span data-ttu-id="b2db1-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2db1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2db1-117">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b2db1-117">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b2db1-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2db1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2db1-119">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2db1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2db1-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="b2db1-120">See also</span></span>

- [<span data-ttu-id="b2db1-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2db1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b2db1-122">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="b2db1-122">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
