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
ms.openlocfilehash: 51d5b2f2ee17cc177e3b0ddc7d2e0b82fd70063d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496370"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a><span data-ttu-id="e40b7-102">ICorProfilerInfo3::GetStringLayout2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e40b7-102">ICorProfilerInfo3::GetStringLayout2 Method</span></span>
<span data-ttu-id="e40b7-103">Získá informace o rozložení objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="e40b7-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e40b7-104">Tato metoda nahrazuje metodu [ICorProfilerInfo2:: GetStringLayout –](icorprofilerinfo2-getstringlayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e40b7-104">This method supersedes the [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40b7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e40b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e40b7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e40b7-106">Parameters</span></span>  
 `pStringLengthOffset`  
 <span data-ttu-id="e40b7-107">mimo Ukazatel na posun umístění relativní vzhledem k `ObjectID` ukazateli, který ukládá délku samotného řetězce.</span><span class="sxs-lookup"><span data-stu-id="e40b7-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e40b7-108">Délka je uložena jako `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="e40b7-108">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e40b7-109">mimo Ukazatel na posun vyrovnávací paměti vzhledem k `ObjectID` ukazateli, který ukládá řetězec velkých znaků.</span><span class="sxs-lookup"><span data-stu-id="e40b7-109">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, which stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e40b7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e40b7-110">Remarks</span></span>  
 <span data-ttu-id="e40b7-111">Řetězce můžou nebo nemusí být zakončené znakem null.</span><span class="sxs-lookup"><span data-stu-id="e40b7-111">Strings may or may not be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40b7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e40b7-112">Requirements</span></span>  
 <span data-ttu-id="e40b7-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e40b7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e40b7-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e40b7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e40b7-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e40b7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e40b7-116">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e40b7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e40b7-117">See also</span></span>

- [<span data-ttu-id="e40b7-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e40b7-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="e40b7-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e40b7-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
