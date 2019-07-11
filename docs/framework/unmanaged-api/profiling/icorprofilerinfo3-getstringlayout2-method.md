---
title: ICorProfilerInfo3::GetStringLayout2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765403"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="d6db6-102">ICorProfilerInfo3::GetStringLayout2 – metoda</span><span class="sxs-lookup"><span data-stu-id="d6db6-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="d6db6-103">Získá informace o rozložení objektu string.</span><span class="sxs-lookup"><span data-stu-id="d6db6-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="d6db6-104">Tato metoda nahrazuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d6db6-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6db6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6db6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6db6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6db6-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="d6db6-107">[out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku samotný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d6db6-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="d6db6-108">Délka se ukládá jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="d6db6-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="d6db6-109">[out] Ukazatel na posun vyrovnávací paměti, relativní k `ObjectID` ukazatel, který ukládá řetězec širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="d6db6-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6db6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6db6-110">Remarks</span></span>  
 <span data-ttu-id="d6db6-111">Řetězce může nebo nemusí být zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d6db6-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6db6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6db6-112">Requirements</span></span>  
 <span data-ttu-id="d6db6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6db6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6db6-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6db6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6db6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6db6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6db6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6db6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6db6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6db6-117">See also</span></span>

- [<span data-ttu-id="d6db6-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6db6-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d6db6-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d6db6-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
