---
title: "ICorProfilerInfo::GetInprocInspectionIThisThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionIThisThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c36688af3ab8941a7004061add8598a480f3e202
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="56f9f-102">ICorProfilerInfo::GetInprocInspectionIThisThread – metoda</span><span class="sxs-lookup"><span data-stu-id="56f9f-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="56f9f-103">Získá objekt, který může být dotazován pro rozhraní ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="56f9f-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="56f9f-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="56f9f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f9f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f9f-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56f9f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56f9f-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="56f9f-107">[out](/cpp/atl/iunknown) objekt, který může být dotázán na `ICorDebugThread` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56f9f-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56f9f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56f9f-108">Remarks</span></span>  
 <span data-ttu-id="56f9f-109">Modul CLR (CLR) ladění služeb podporované omezené v procesu ladění v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="56f9f-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="56f9f-110">V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="56f9f-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="56f9f-111">V důsledku názory zákazníků v procesu ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.</span><span class="sxs-lookup"><span data-stu-id="56f9f-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f9f-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f9f-112">Requirements</span></span>  
 <span data-ttu-id="56f9f-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56f9f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56f9f-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="56f9f-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="56f9f-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56f9f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56f9f-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="56f9f-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56f9f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="56f9f-117">See Also</span></span>  
 [<span data-ttu-id="56f9f-118">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56f9f-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
