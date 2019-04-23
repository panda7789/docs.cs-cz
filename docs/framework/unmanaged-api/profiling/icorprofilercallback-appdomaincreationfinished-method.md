---
title: ICorProfilerCallback::AppDomainCreationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35dac5fd000f5ae30af917e3813239b2e365e64a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153982"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="2d9b8-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="2d9b8-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="2d9b8-103">Upozornění profileru vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d9b8-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="2d9b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d9b8-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="2d9b8-106">[in] Určuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2d9b8-107">[in] HRESULT, která určuje, zda vytváření domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d9b8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d9b8-108">Remarks</span></span>  
 <span data-ttu-id="2d9b8-109">ID aplikace není platná pro všechny žádost o informace, dokud `AppDomainCreationFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="2d9b8-110">Některé části načtení domény aplikace může pokračovat po `AppDomainCreationFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="2d9b8-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2d9b8-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část vytváření domény aplikace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="2d9b8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d9b8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d9b8-113">Requirements</span></span>  
 <span data-ttu-id="2d9b8-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d9b8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d9b8-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d9b8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d9b8-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d9b8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d9b8-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d9b8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9b8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d9b8-118">See also</span></span>

- [<span data-ttu-id="2d9b8-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d9b8-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
