---
title: ICorProfilerInfo::GetFunctionFromToken – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f76059387f00316888cbe6d839bece33e3eef9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520261"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="e71e9-102">ICorProfilerInfo::GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="e71e9-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="e71e9-103">Získá ID funkce.</span><span class="sxs-lookup"><span data-stu-id="e71e9-103">Gets the ID of a function.</span></span> <span data-ttu-id="e71e9-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="e71e9-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="e71e9-105">Použití [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e71e9-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e71e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e71e9-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="e71e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e71e9-107">Remarks</span></span>  
 <span data-ttu-id="e71e9-108">`GetFunctionFromToken` Metoda nebude fungovat pro obecné funkce nebo funkce v obecných typech; je nyní zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e71e9-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="e71e9-109">Použití `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pro všechny funkce.</span><span class="sxs-lookup"><span data-stu-id="e71e9-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e71e9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e71e9-110">Requirements</span></span>  
 <span data-ttu-id="e71e9-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e71e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e71e9-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e71e9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e71e9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e71e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e71e9-114">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="e71e9-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e71e9-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e71e9-115">See also</span></span>
- [<span data-ttu-id="e71e9-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e71e9-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
