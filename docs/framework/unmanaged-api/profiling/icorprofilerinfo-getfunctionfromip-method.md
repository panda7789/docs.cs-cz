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
ms.openlocfilehash: 339c5db1610a3cf087085ce19fc663436d9c4ec1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498307"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="8e451-102">ICorProfilerInfo::GetFunctionFromIP – metoda</span><span class="sxs-lookup"><span data-stu-id="8e451-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="8e451-103">Mapuje ukazatel na instrukci spravovaného kódu na `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="8e451-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e451-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e451-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e451-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e451-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="8e451-106">\[in] ukazatel na instrukci ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="8e451-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="8e451-107">\[out] vrácené ID funkce.</span><span class="sxs-lookup"><span data-stu-id="8e451-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e451-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e451-108">Requirements</span></span>  
 <span data-ttu-id="8e451-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e451-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e451-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8e451-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8e451-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e451-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e451-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e451-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e451-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e451-113">See also</span></span>

- [<span data-ttu-id="8e451-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8e451-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
