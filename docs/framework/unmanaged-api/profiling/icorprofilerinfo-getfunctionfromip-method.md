---
title: ICorProfilerInfo::GetFunctionFromIP – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9fec1d1effbf900974327247078b65f60fef7e21
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466424"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="fb71c-102">ICorProfilerInfo::GetFunctionFromIP – metoda</span><span class="sxs-lookup"><span data-stu-id="fb71c-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="fb71c-103">Mapuje ukazatel instrukce spravovaného kódu `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="fb71c-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb71c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb71c-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb71c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fb71c-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="fb71c-106">[in] Ukazatele na instrukci ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="fb71c-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="fb71c-107">[out] ID vrácené funkce.</span><span class="sxs-lookup"><span data-stu-id="fb71c-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb71c-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fb71c-108">Requirements</span></span>  
 <span data-ttu-id="fb71c-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb71c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb71c-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb71c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb71c-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb71c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb71c-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb71c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb71c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb71c-113">See also</span></span>
- [<span data-ttu-id="fb71c-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fb71c-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
