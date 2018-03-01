---
title: "ICorProfilerInfo::GetFunctionFromToken – metoda"
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
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c90a63f075c392ca3ff02a47190f9c4dfe6aad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="4d217-102">ICorProfilerInfo::GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="4d217-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="4d217-103">Získá ID funkce.</span><span class="sxs-lookup"><span data-stu-id="4d217-103">Gets the ID of a function.</span></span> <span data-ttu-id="4d217-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="4d217-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4d217-105">Použití [ICorProfilerInfo2::getfunctionfromtokenandtypeargs –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="4d217-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d217-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d217-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4d217-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d217-107">Remarks</span></span>  
 <span data-ttu-id="4d217-108">`GetFunctionFromToken` Metoda nebude fungovat pro obecné funkce nebo funkce v obecných typech; je nyní zastaralá.</span><span class="sxs-lookup"><span data-stu-id="4d217-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="4d217-109">Použití `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pro všechny funkce.</span><span class="sxs-lookup"><span data-stu-id="4d217-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d217-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d217-110">Requirements</span></span>  
 <span data-ttu-id="4d217-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d217-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d217-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d217-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d217-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d217-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d217-114">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="4d217-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d217-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d217-115">See Also</span></span>  
 [<span data-ttu-id="4d217-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d217-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
