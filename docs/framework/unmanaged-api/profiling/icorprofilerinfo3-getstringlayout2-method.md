---
title: "ICorProfilerInfo3::GetStringLayout2 – metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 97f4ab9eefa8bf1f2b3a5057f24b6a940ba91f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="79c69-102">ICorProfilerInfo3::GetStringLayout2 – metoda</span><span class="sxs-lookup"><span data-stu-id="79c69-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="79c69-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="79c69-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="79c69-104">Tato metoda nahrazuje [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="79c69-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79c69-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79c69-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79c69-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="79c69-107">[out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, uchovávající délky řetězce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="79c69-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="79c69-108">Délka se ukládají jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="79c69-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="79c69-109">[out] Ukazatel na posun vyrovnávací paměti, relativně k `ObjectID` ukazatele, který ukládá řetězec široké znaky.</span><span class="sxs-lookup"><span data-stu-id="79c69-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c69-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79c69-110">Remarks</span></span>  
 <span data-ttu-id="79c69-111">Řetězce mohou nebo nemusí být ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="79c69-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c69-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79c69-112">Requirements</span></span>  
 <span data-ttu-id="79c69-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79c69-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c69-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79c69-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79c69-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79c69-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c69-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c69-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c69-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="79c69-117">See Also</span></span>  
 [<span data-ttu-id="79c69-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79c69-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="79c69-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="79c69-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
