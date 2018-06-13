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
ms.openlocfilehash: 57a21a3e4c1324e15a8418dacb8cfe7c5163f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454401"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="173d7-102">ICorProfilerInfo3::GetStringLayout2 – metoda</span><span class="sxs-lookup"><span data-stu-id="173d7-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="173d7-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="173d7-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="173d7-104">Tato metoda nahrazuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="173d7-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="173d7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="173d7-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="173d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="173d7-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="173d7-107">[out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, uchovávající délky řetězce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="173d7-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="173d7-108">Délka se ukládají jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="173d7-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="173d7-109">[out] Ukazatel na posun vyrovnávací paměti, relativně k `ObjectID` ukazatele, který ukládá řetězec široké znaky.</span><span class="sxs-lookup"><span data-stu-id="173d7-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="173d7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="173d7-110">Remarks</span></span>  
 <span data-ttu-id="173d7-111">Řetězce mohou nebo nemusí být ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="173d7-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="173d7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="173d7-112">Requirements</span></span>  
 <span data-ttu-id="173d7-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="173d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="173d7-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="173d7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="173d7-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="173d7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="173d7-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="173d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="173d7-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="173d7-117">See Also</span></span>  
 [<span data-ttu-id="173d7-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="173d7-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="173d7-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="173d7-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
