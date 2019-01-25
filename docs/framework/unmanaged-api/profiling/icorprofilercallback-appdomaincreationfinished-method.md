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
ms.openlocfilehash: 48d43d9107d010b12167b977acd2e500437c039f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501709"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="e475b-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e475b-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="e475b-103">Upozornění profileru vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e475b-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e475b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e475b-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e475b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e475b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e475b-106">[in] Určuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="e475b-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e475b-107">[in] HRESULT, která určuje, zda vytváření domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="e475b-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e475b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e475b-108">Remarks</span></span>  
 <span data-ttu-id="e475b-109">ID aplikace není platná pro všechny žádost o informace, dokud `AppDomainCreationFinished` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="e475b-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="e475b-110">Některé části načtení domény aplikace může pokračovat po `AppDomainCreationFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e475b-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="e475b-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="e475b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e475b-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část vytváření domény aplikace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="e475b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e475b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e475b-113">Requirements</span></span>  
 <span data-ttu-id="e475b-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e475b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e475b-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e475b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e475b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e475b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e475b-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e475b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e475b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e475b-118">See also</span></span>
- [<span data-ttu-id="e475b-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e475b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
