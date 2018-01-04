---
title: "CorpubPublish – třída typu coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorpubPublish Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CorpubPublish
helpviewer_keywords: CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3dec1175715bdbddc3c975924e91e238fa6d5f3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="2e7f6-102">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="2e7f6-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="2e7f6-103">Poskytuje rozhraní pro publikování informací o doménách aplikace a procesy.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e7f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e7f6-104">Syntax</span></span>  
  
```  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="2e7f6-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-105">Interfaces</span></span>  
  
|<span data-ttu-id="2e7f6-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-106">Interface</span></span>|<span data-ttu-id="2e7f6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2e7f6-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="2e7f6-108">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="2e7f6-109">Poskytuje metody pro publikování informací o procesy a aplikační domény v těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="2e7f6-110">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="2e7f6-111">Reprezentuje a poskytuje informace o doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="2e7f6-112">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="2e7f6-113">Poskytuje metody, které překračují kolekce aplikační domény, které existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="2e7f6-114">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="2e7f6-115">Představuje proces, který běží na počítači.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="2e7f6-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e7f6-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="2e7f6-117">Poskytuje metody, které překračují kolekce procesy, které jsou spuštěny v počítači.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e7f6-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e7f6-118">Remarks</span></span>  
 <span data-ttu-id="2e7f6-119">Typický scénář publikování zahrnuje vývojáři, který chce ladění spravovaného kódu, který běží na počítači v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="2e7f6-120">Hostitelské prostředí může používat více než jedné domény aplikace v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="2e7f6-121">Vývojář se má použít grafické uživatelské rozhraní nebo jiných prostředků k zobrazení seznamu všech procesů, které jsou spuštěné v počítači a vyberte konkrétní proces.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="2e7f6-122">Seznam by měly obsahovat všechny domény aplikace v rámci procesy, které běží spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="2e7f6-123">Vývojář můžete identifikovat specifické aplikační doméně a připojit ladicí program k této doméně.</span><span class="sxs-lookup"><span data-stu-id="2e7f6-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e7f6-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e7f6-124">Requirements</span></span>  
 <span data-ttu-id="2e7f6-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e7f6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e7f6-126">**Záhlaví:** CorPub.idl</span><span class="sxs-lookup"><span data-stu-id="2e7f6-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="2e7f6-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e7f6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e7f6-128">**Verze rozhraní .NET framework:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e7f6-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7f6-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e7f6-129">See Also</span></span>  
 [<span data-ttu-id="2e7f6-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="2e7f6-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
