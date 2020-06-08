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
ms.openlocfilehash: 76f56971223154d3ed966c272081049adf30de54
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500491"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="e7d6c-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="e7d6c-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="e7d6c-103">Oznamuje profileru, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7d6c-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7d6c-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="e7d6c-106">\[v] identifikuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="e7d6c-107">\[in] HRESULT, který označuje, zda bylo úspěšně vytvořeno vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7d6c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7d6c-108">Remarks</span></span>  
 <span data-ttu-id="e7d6c-109">ID aplikace není platné pro žádnou žádost o informace, dokud `AppDomainCreationFinished` není volána metoda.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="e7d6c-110">Některé části načtení aplikační domény můžou pokračovat i po `AppDomainCreationFinished` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="e7d6c-111">Neúspěšná hodnota HRESULT v `hrStatus` znamená selhání.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e7d6c-112">Úspěch HRESULT v v `hrStatus` znamená pouze to, že první část vytváření domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="e7d6c-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d6c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7d6c-113">Requirements</span></span>  
 <span data-ttu-id="e7d6c-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7d6c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d6c-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7d6c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7d6c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e7d6c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d6c-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d6c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d6c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7d6c-118">See also</span></span>

- [<span data-ttu-id="e7d6c-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7d6c-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
