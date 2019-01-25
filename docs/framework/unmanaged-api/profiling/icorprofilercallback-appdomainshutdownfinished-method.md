---
title: ICorProfilerCallback::AppDomainShutdownFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c89a7671cde9e519d0fc66751ee8f95b34fe9039
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669663"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="42155-102">ICorProfilerCallback::AppDomainShutdownFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="42155-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="42155-103">Oznámí profileru, že byl odpojen od procesu domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="42155-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42155-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42155-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42155-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42155-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="42155-106">[in] Určuje doménu, ve kterém jsou uložené sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="42155-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="42155-107">[in] HRESULT, která určuje, zda byla doména aplikace úspěšně odpojen.</span><span class="sxs-lookup"><span data-stu-id="42155-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42155-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42155-108">Remarks</span></span>  
 <span data-ttu-id="42155-109">Hodnota `appDomainId` není platná pro požadavek informace po [icorprofilercallback::appdomainshutdownstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) metoda vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="42155-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="42155-110">Některé části uvolnění domény aplikace může pokračovat po `AppDomainCreationFinished` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="42155-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="42155-111">Selhání hodnoty HRESULT v `hrStatus` naznačuje chybu.</span><span class="sxs-lookup"><span data-stu-id="42155-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="42155-112">Ale úspěch HRESULT v `hrStatus` značí pouze, že první část uvolnění domény aplikace proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="42155-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42155-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42155-113">Requirements</span></span>  
 <span data-ttu-id="42155-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42155-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42155-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42155-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42155-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42155-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42155-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42155-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42155-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42155-118">See also</span></span>
- [<span data-ttu-id="42155-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="42155-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
