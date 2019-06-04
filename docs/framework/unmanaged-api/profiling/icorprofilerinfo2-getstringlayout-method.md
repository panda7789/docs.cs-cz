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
ms.openlocfilehash: faa5ecf63ac3795a58369d94f9fb15f853edb576
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490708"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="3bfb8-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="3bfb8-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="3bfb8-103">Získá informace o rozložení objektu string.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="3bfb8-104">Tato metoda je zastaralé v rozhraní .NET Framework 4 a je nahrazen technologií [icorprofilerinfo3::getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bfb8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bfb8-105">Syntax</span></span>  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bfb8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bfb8-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="3bfb8-107">[out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="3bfb8-108">Délka se ukládá jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bfb8-109">Tento parametr vrátí délku řetězce, nikoli délka vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="3bfb8-110">Délka vyrovnávací paměti je už k dispozici.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="3bfb8-111">[out] Ukazatel na posun umístění vzhledem ke `ObjectID` ukazatel, který ukládá délku samotný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="3bfb8-112">Délka se ukládá jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="3bfb8-113">[out] Ukazatel na posun vyrovnávací paměti, relativní k `ObjectID` ukazatel, který ukládá řetězec širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bfb8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bfb8-114">Remarks</span></span>  
 <span data-ttu-id="3bfb8-115">`GetStringLayout` Metoda získá posuny, vzhledem k `ObjectID` ukazatele z umístění, ve kterých se ukládají následující:</span><span class="sxs-lookup"><span data-stu-id="3bfb8-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="3bfb8-116">Délka vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="3bfb8-117">Délka samotný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="3bfb8-118">Vyrovnávací paměť, která obsahuje skutečné řetězec širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="3bfb8-119">Řetězce můžou být zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3bfb8-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bfb8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bfb8-120">Requirements</span></span>  
 <span data-ttu-id="3bfb8-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bfb8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bfb8-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bfb8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bfb8-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bfb8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bfb8-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bfb8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bfb8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bfb8-125">See also</span></span>

- [<span data-ttu-id="3bfb8-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bfb8-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3bfb8-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3bfb8-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
