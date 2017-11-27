---
title: "ICorProfilerInfo::BeginInprocDebugging – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.BeginInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c7c0b3c0a20c98b9ca2e5dd5ea51053008e415a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="4c65b-102">ICorProfilerInfo::BeginInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="4c65b-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="4c65b-103">Inicializuje ladění podpory v procesu.</span><span class="sxs-lookup"><span data-stu-id="4c65b-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="4c65b-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="4c65b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c65b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c65b-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c65b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c65b-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="4c65b-107">[v] Nastavte tuto hodnotu na `true` inicializovat ladění podporu pro pouze aktuální vlákno; nastavte ji na `false` inicializovat ladění podporu pro všechna vlákna.</span><span class="sxs-lookup"><span data-stu-id="4c65b-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="4c65b-108">[out] Ukazatel na vrácené hodnoty, který identifikuje relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="4c65b-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c65b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c65b-109">Remarks</span></span>  
 <span data-ttu-id="4c65b-110">Ladění služby CLR podporované omezené v procesu ladění v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="4c65b-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="4c65b-111">V procesu ladění povoleno profileru používat části kontroly rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="4c65b-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4c65b-112">Však z důvodu zpětné vazby zákazníka, v rámci procesu ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a nahradí sadu funkcí, které je větší souladu profilaci API.</span><span class="sxs-lookup"><span data-stu-id="4c65b-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c65b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c65b-113">Requirements</span></span>  
 <span data-ttu-id="4c65b-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c65b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c65b-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c65b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c65b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c65b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c65b-117">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="4c65b-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c65b-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c65b-118">See Also</span></span>  
 [<span data-ttu-id="4c65b-119">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c65b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
