---
title: "ICorProfilerInfo2::GetStringLayout – metoda"
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
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ad91829fab31b47a1dd51bb6cc9118c2ebe4c3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="bee54-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="bee54-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="bee54-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="bee54-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="bee54-104">Tato metoda je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]a je nahrazena [icorprofilerinfo3::getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="bee54-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee54-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee54-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bee54-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bee54-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="bee54-107">[out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, který ukládá délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="bee54-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="bee54-108">Délka se ukládají jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bee54-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bee54-109">Tento parametr vrátí délku řetězce samostatně, není délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bee54-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="bee54-110">Délka vyrovnávací paměti je již k dispozici.</span><span class="sxs-lookup"><span data-stu-id="bee54-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="bee54-111">[out] Ukazatel na posun umístění relativně k `ObjectID` ukazatele, uchovávající délky řetězce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="bee54-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="bee54-112">Délka se ukládají jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="bee54-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="bee54-113">[out] Ukazatel na posun vyrovnávací paměti, relativně k `ObjectID` ukazatele, který ukládá řetězec široké znaky.</span><span class="sxs-lookup"><span data-stu-id="bee54-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bee54-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bee54-114">Remarks</span></span>  
 <span data-ttu-id="bee54-115">`GetStringLayout` Metoda získá posun, vzhledem k `ObjectID` ukazatele, umístění, ve kterých se ukládají následující:</span><span class="sxs-lookup"><span data-stu-id="bee54-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
-   <span data-ttu-id="bee54-116">Délka vyrovnávací paměti řetězec.</span><span class="sxs-lookup"><span data-stu-id="bee54-116">The length of the string's buffer.</span></span>  
  
-   <span data-ttu-id="bee54-117">Délka řetězce sám sebe.</span><span class="sxs-lookup"><span data-stu-id="bee54-117">The length of the string itself.</span></span>  
  
-   <span data-ttu-id="bee54-118">Vyrovnávací paměť, která obsahuje konkrétní řetězec široké znaky.</span><span class="sxs-lookup"><span data-stu-id="bee54-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="bee54-119">Řetězce může být ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="bee54-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bee54-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bee54-120">Requirements</span></span>  
 <span data-ttu-id="bee54-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee54-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee54-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bee54-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bee54-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bee54-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bee54-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee54-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee54-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bee54-125">See Also</span></span>  
 [<span data-ttu-id="bee54-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee54-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="bee54-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee54-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
