---
title: "ICorProfilerInfo::EndInprocDebugging – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a36c557d9ab2fa661808aa2f0be942d11ea9fa61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="47f32-102">ICorProfilerInfo::EndInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="47f32-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="47f32-103">Ukončí relaci ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="47f32-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="47f32-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="47f32-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f32-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47f32-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47f32-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47f32-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="47f32-107">[v] Hodnota, která identifikuje relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="47f32-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="47f32-108">Tato hodnota musí být stejný jako dostali [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="47f32-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47f32-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47f32-109">Remarks</span></span>  
 <span data-ttu-id="47f32-110">Je třeba volat [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="47f32-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="47f32-111">Ladění služby CLR podporované omezené v procesu ladění v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="47f32-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="47f32-112">V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="47f32-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="47f32-113">Však z důvodu zpětné vazby zákazníka, v rámci procesu ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.</span><span class="sxs-lookup"><span data-stu-id="47f32-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f32-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47f32-114">Requirements</span></span>  
 <span data-ttu-id="47f32-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47f32-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f32-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47f32-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47f32-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47f32-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47f32-118">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="47f32-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f32-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="47f32-119">See Also</span></span>  
 [<span data-ttu-id="47f32-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47f32-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
