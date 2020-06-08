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
ms.openlocfilehash: 18c3b6e840ec1f6cb1481c8d752e6399dcdae077
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498138"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="52eee-102">ICorProfilerInfo::GetFunctionFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="52eee-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="52eee-103">Získá ID funkce.</span><span class="sxs-lookup"><span data-stu-id="52eee-103">Gets the ID of a function.</span></span> <span data-ttu-id="52eee-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="52eee-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="52eee-105">Místo toho použijte metodu [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs –](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52eee-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52eee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52eee-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="52eee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52eee-107">Remarks</span></span>  
 <span data-ttu-id="52eee-108">`GetFunctionFromToken`Metoda nebude fungovat pro obecné funkce nebo funkce v obecných typech; je nyní zastaralá.</span><span class="sxs-lookup"><span data-stu-id="52eee-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="52eee-109">Použijte `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` pro všechny funkce.</span><span class="sxs-lookup"><span data-stu-id="52eee-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52eee-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52eee-110">Requirements</span></span>  
 <span data-ttu-id="52eee-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52eee-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52eee-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="52eee-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52eee-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="52eee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52eee-114">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="52eee-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eee-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52eee-115">See also</span></span>

- [<span data-ttu-id="52eee-116">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52eee-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
