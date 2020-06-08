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
ms.openlocfilehash: 257cf24fa476c75d6ec949e17a5b83fc015b8d43
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496778"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="5515b-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="5515b-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="5515b-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="5515b-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="5515b-104">Tato metoda je zastaralá v .NET Framework 4 a nahrazuje se metodou [ICorProfilerInfo3:: getstringlayout2 –](icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5515b-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5515b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5515b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5515b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5515b-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="5515b-107">mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="5515b-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="5515b-108">Délka je uložena jako `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="5515b-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5515b-109">Tento parametr vrátí délku samotného řetězce, nikoli délku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5515b-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="5515b-110">Délka vyrovnávací paměti již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5515b-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="5515b-111">mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="5515b-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="5515b-112">Délka je uložena jako `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="5515b-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="5515b-113">mimo Ukazatel na posun vyrovnávací paměti vzhledem k `ObjectID` ukazateli, který ukládá řetězec znaků v šířce.</span><span class="sxs-lookup"><span data-stu-id="5515b-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5515b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5515b-114">Remarks</span></span>  
 <span data-ttu-id="5515b-115">`GetStringLayout`Metoda získá posuny relativní vzhledem k `ObjectID` ukazateli umístění, ve kterých jsou uloženy následující:</span><span class="sxs-lookup"><span data-stu-id="5515b-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="5515b-116">Délka vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="5515b-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="5515b-117">Délka samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="5515b-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="5515b-118">Vyrovnávací paměť, která obsahuje skutečný řetězec velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="5515b-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="5515b-119">Řetězce můžou být zakončené znakem null.</span><span class="sxs-lookup"><span data-stu-id="5515b-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5515b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5515b-120">Requirements</span></span>  
 <span data-ttu-id="5515b-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5515b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5515b-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5515b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5515b-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5515b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5515b-124">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5515b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5515b-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5515b-125">See also</span></span>

- [<span data-ttu-id="5515b-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5515b-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5515b-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5515b-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
