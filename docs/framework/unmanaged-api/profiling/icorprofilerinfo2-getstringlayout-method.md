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
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963795"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="46af8-102">ICorProfilerInfo2::GetStringLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="46af8-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="46af8-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="46af8-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="46af8-104">Tato metoda je zastaralá v .NET Framework 4 a nahrazuje se metodou [ICorProfilerInfo3:: getstringlayout2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="46af8-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46af8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46af8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46af8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="46af8-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="46af8-107">mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="46af8-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="46af8-108">Délka je uložena jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="46af8-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46af8-109">Tento parametr vrátí délku samotného řetězce, nikoli délku vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="46af8-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="46af8-110">Délka vyrovnávací paměti již není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="46af8-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="46af8-111">mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="46af8-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="46af8-112">Délka je uložena jako `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="46af8-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="46af8-113">mimo Ukazatel na posun vyrovnávací paměti vzhledem k `ObjectID` ukazateli, který ukládá řetězec znaků v šířce.</span><span class="sxs-lookup"><span data-stu-id="46af8-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46af8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46af8-114">Remarks</span></span>  
 <span data-ttu-id="46af8-115">Metoda získá posuny relativní vzhledem `ObjectID` k ukazateli umístění, ve kterých jsou uloženy následující: `GetStringLayout`</span><span class="sxs-lookup"><span data-stu-id="46af8-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="46af8-116">Délka vyrovnávací paměti řetězce.</span><span class="sxs-lookup"><span data-stu-id="46af8-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="46af8-117">Délka samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="46af8-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="46af8-118">Vyrovnávací paměť, která obsahuje skutečný řetězec velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="46af8-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="46af8-119">Řetězce můžou být zakončené znakem null.</span><span class="sxs-lookup"><span data-stu-id="46af8-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46af8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46af8-120">Requirements</span></span>  
 <span data-ttu-id="46af8-121">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46af8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46af8-122">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46af8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46af8-123">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46af8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46af8-124">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46af8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46af8-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46af8-125">See also</span></span>

- [<span data-ttu-id="46af8-126">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46af8-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="46af8-127">ICorProfilerInfo2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="46af8-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
