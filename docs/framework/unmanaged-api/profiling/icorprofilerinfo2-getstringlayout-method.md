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
ms.openlocfilehash: 537840ac03b4136682b78cb964950ab5670a7d7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868613"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="53fb0-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="53fb0-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="53fb0-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="53fb0-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="53fb0-104">Tato metoda je zastaralá v .NET Framework 4 a nahrazuje se metodou [ICorProfilerInfo3:: getstringlayout2 –](icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="53fb0-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fb0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53fb0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53fb0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="53fb0-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="53fb0-107">mimo Ukazatel na posun umístění vzhledem k ukazateli `ObjectID`, který ukládá délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="53fb0-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="53fb0-108">Délka je uložena jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="53fb0-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53fb0-109">Tento parametr vrátí délku samotného řetězce, nikoli délku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="53fb0-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="53fb0-110">Délka vyrovnávací paměti již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="53fb0-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="53fb0-111">mimo Ukazatel na posun umístění vzhledem k ukazateli `ObjectID`, který ukládá délku samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="53fb0-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="53fb0-112">Délka je uložena jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="53fb0-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="53fb0-113">mimo Ukazatel na posun vyrovnávací paměti vzhledem k ukazateli `ObjectID`, který ukládá řetězec velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="53fb0-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53fb0-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53fb0-114">Remarks</span></span>  
 <span data-ttu-id="53fb0-115">Metoda `GetStringLayout` získá posuny relativní k ukazateli `ObjectID` na místech, kde jsou uložena následující:</span><span class="sxs-lookup"><span data-stu-id="53fb0-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="53fb0-116">Délka vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="53fb0-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="53fb0-117">Délka samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="53fb0-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="53fb0-118">Vyrovnávací paměť, která obsahuje skutečný řetězec velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="53fb0-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="53fb0-119">Řetězce můžou být zakončené znakem null.</span><span class="sxs-lookup"><span data-stu-id="53fb0-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53fb0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="53fb0-120">Requirements</span></span>  
 <span data-ttu-id="53fb0-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53fb0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53fb0-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="53fb0-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53fb0-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="53fb0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53fb0-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53fb0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fb0-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53fb0-125">See also</span></span>

- [<span data-ttu-id="53fb0-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53fb0-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="53fb0-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="53fb0-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
