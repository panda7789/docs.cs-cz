---
title: "ICorProfilerInfo::GetInprocInspectionInterface – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetInprocInspectionInterface
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type: apiref
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be114784b0003e5f1540520fdbbef751b369f1da
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="e9753-102">ICorProfilerInfo::GetInprocInspectionInterface – metoda</span><span class="sxs-lookup"><span data-stu-id="e9753-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="e9753-103">Získá objekt, který může být dotazován pro rozhraní "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="e9753-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="e9753-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e9753-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9753-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9753-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9753-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9753-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="e9753-107">[out](/cpp/atl/iunknown) objekt, který může být dotazován pro `ICorDebugProcess` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9753-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9753-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9753-108">Remarks</span></span>  
 <span data-ttu-id="e9753-109">Modul CLR (CLR) rozhraní API pro ladění podporována omezené v procesu ladění v rozhraní .NET Framework verze 1.0.</span><span class="sxs-lookup"><span data-stu-id="e9753-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="e9753-110">V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="e9753-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="e9753-111">V důsledku názory zákazníků v procesu ladění bylo odstraněno z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.</span><span class="sxs-lookup"><span data-stu-id="e9753-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9753-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9753-112">Requirements</span></span>  
 <span data-ttu-id="e9753-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9753-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9753-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9753-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9753-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9753-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9753-116">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e9753-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9753-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9753-117">See Also</span></span>  
 [<span data-ttu-id="e9753-118">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9753-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
