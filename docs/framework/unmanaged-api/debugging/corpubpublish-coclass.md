---
title: CorpubPublish – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132142"
---
# <a name="corpubpublish-coclass"></a><span data-ttu-id="6c944-102">CorpubPublish – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="6c944-102">CorpubPublish Coclass</span></span>
<span data-ttu-id="6c944-103">Poskytuje rozhraní pro publikování informací o aplikačních doménách a procesech.</span><span class="sxs-lookup"><span data-stu-id="6c944-103">Provides interfaces for publishing information about application domains and processes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c944-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c944-104">Syntax</span></span>  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="6c944-105">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-105">Interfaces</span></span>  
  
|<span data-ttu-id="6c944-106">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-106">Interface</span></span>|<span data-ttu-id="6c944-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6c944-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="6c944-108">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-108">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|<span data-ttu-id="6c944-109">Poskytuje metody pro publikování informací o procesech a doménách aplikace v těchto procesech.</span><span class="sxs-lookup"><span data-stu-id="6c944-109">Provides methods for publishing information about processes and the application domains in those processes.</span></span>|  
|[<span data-ttu-id="6c944-110">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-110">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|<span data-ttu-id="6c944-111">Představuje a poskytuje informace o doméně aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="6c944-111">Represents, and provides information about, an application domain in a process.</span></span>|  
|[<span data-ttu-id="6c944-112">ICorPublishAppDomainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-112">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|<span data-ttu-id="6c944-113">Poskytuje metody, které procházejí kolekci aplikačních domén, které aktuálně existují v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6c944-113">Provides methods that traverse a collection of application domains that currently exist within a process.</span></span>|  
|[<span data-ttu-id="6c944-114">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-114">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|<span data-ttu-id="6c944-115">Představuje proces, který je spuštěn v počítači.</span><span class="sxs-lookup"><span data-stu-id="6c944-115">Represents a process that is running on a computer.</span></span>|  
|[<span data-ttu-id="6c944-116">ICorPublishProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c944-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|<span data-ttu-id="6c944-117">Poskytuje metody, které procházejí kolekci procesů, které jsou spuštěny v počítači.</span><span class="sxs-lookup"><span data-stu-id="6c944-117">Provides methods that traverse a collection of processes that are running on a computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c944-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c944-118">Remarks</span></span>  
 <span data-ttu-id="6c944-119">Typický scénář publikování zahrnuje vývojáře, který chce ladit spravovaný kód, který je spuštěný v počítači v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c944-119">A typical publishing scenario involves a developer who wants to debug managed code that is running on a computer within an application domain.</span></span> <span data-ttu-id="6c944-120">Hostující prostředí může v rámci procesu používat více než jednu doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c944-120">The hosting environment may be running more than one application domain within a process.</span></span> <span data-ttu-id="6c944-121">Vývojář chce použít grafické uživatelské rozhraní nebo jiné prostředky k zobrazení seznamu všech procesů spuštěných v počítači a vybrat konkrétní proces.</span><span class="sxs-lookup"><span data-stu-id="6c944-121">The developer would like to use a graphical user interface or some other means to list all of the processes that are running on the computer, and pick a specific process.</span></span> <span data-ttu-id="6c944-122">Výpis by měl obsahovat všechny domény aplikace v rámci procesů, na kterých běží spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="6c944-122">The listing should include all of the application domains within processes that are running managed code.</span></span> <span data-ttu-id="6c944-123">Vývojář pak může identifikovat konkrétní doménu aplikace a připojit ladicí program k této doméně.</span><span class="sxs-lookup"><span data-stu-id="6c944-123">The developer can then identify the specific application domain and attach a debugger to that domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c944-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c944-124">Requirements</span></span>  
 <span data-ttu-id="6c944-125">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c944-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c944-126">**Hlavička:** CorPub. idl</span><span class="sxs-lookup"><span data-stu-id="6c944-126">**Header:** CorPub.idl</span></span>  
  
 <span data-ttu-id="6c944-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c944-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c944-128">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c944-128">**.NET Framework Versions:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c944-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c944-129">See also</span></span>

- [<span data-ttu-id="6c944-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="6c944-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
