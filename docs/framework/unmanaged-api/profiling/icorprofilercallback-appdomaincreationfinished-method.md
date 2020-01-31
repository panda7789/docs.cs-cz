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
ms.openlocfilehash: 1cf3f2b62b388b6c2d6fcd75b1b07a67d5b2e49f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866699"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="147c4-102">ICorProfilerCallback::AppDomainCreationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="147c4-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="147c4-103">Oznamuje profileru, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="147c4-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="147c4-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="147c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="147c4-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="147c4-106">\[v] identifikuje doménu, která byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="147c4-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="147c4-107">\[in] hodnota HRESULT, která indikuje, jestli se úspěšně dokončilo vytváření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="147c4-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="147c4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="147c4-108">Remarks</span></span>  
 <span data-ttu-id="147c4-109">ID aplikace není platné pro žádnou žádost o informace, dokud není volána metoda `AppDomainCreationFinished`.</span><span class="sxs-lookup"><span data-stu-id="147c4-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="147c4-110">Některé části načtení aplikační domény můžou po zpětném volání `AppDomainCreationFinished` pokračovat.</span><span class="sxs-lookup"><span data-stu-id="147c4-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="147c4-111">Selhání HRESULT v `hrStatus` označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="147c4-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="147c4-112">Úspěšnost HRESULT v `hrStatus` však znamená, že první část vytváření domény aplikace byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="147c4-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="147c4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="147c4-113">Requirements</span></span>  
 <span data-ttu-id="147c4-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="147c4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147c4-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="147c4-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="147c4-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="147c4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="147c4-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147c4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147c4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="147c4-118">See also</span></span>

- [<span data-ttu-id="147c4-119">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="147c4-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
