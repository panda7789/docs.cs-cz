---
title: ICorProfilerInfo2::GetStringLayout – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a3d26a99844d00609b28eaef08ff0874a6701fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664969"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="55fcd-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="55fcd-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="55fcd-103">Získá informace o rozložení objektu string.</span><span class="sxs-lookup"><span data-stu-id="55fcd-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="55fcd-104">Tato metoda je zastaralá ve [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]a je nahrazen technologií [icorprofilerinfo3::getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="55fcd-104">This method is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55fcd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55fcd-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55fcd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="55fcd-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="55fcd-107">[out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="55fcd-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="55fcd-108">Délka se ukládá jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="55fcd-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55fcd-109">Tento parametr vrátí délku řetězce, nikoli délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="55fcd-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="55fcd-110">Délka vyrovnávací paměti je už k dispozici.</span><span class="sxs-lookup"><span data-stu-id="55fcd-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="55fcd-111">[out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku samotný řetězec.</span><span class="sxs-lookup"><span data-stu-id="55fcd-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="55fcd-112">Délka se ukládá jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="55fcd-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="55fcd-113">[out] Ukazatel na posun vyrovnávací paměti, relativní k `ObjectID` ukazatel, který ukládá řetězec širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="55fcd-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55fcd-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55fcd-114">Remarks</span></span>  
 <span data-ttu-id="55fcd-115">`GetStringLayout` Metoda získá posuny, vzhledem k `ObjectID` ukazatele z umístění, ve kterých se ukládají následující:</span><span class="sxs-lookup"><span data-stu-id="55fcd-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="55fcd-116">Délka vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="55fcd-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="55fcd-117">Délka samotný řetězec.</span><span class="sxs-lookup"><span data-stu-id="55fcd-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="55fcd-118">Vyrovnávací paměť, která obsahuje skutečné řetězec širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="55fcd-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="55fcd-119">Řetězce můžou být zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="55fcd-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55fcd-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="55fcd-120">Requirements</span></span>  
 <span data-ttu-id="55fcd-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55fcd-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55fcd-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55fcd-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55fcd-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55fcd-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55fcd-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55fcd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fcd-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55fcd-125">See also</span></span>

- [<span data-ttu-id="55fcd-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55fcd-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="55fcd-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="55fcd-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
