---
title: ICorProfilerInfo::GetCodeInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498359"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="cf1a3-102">ICorProfilerInfo::GetCodeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="cf1a3-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="cf1a3-103">Získá rozsah nativního kódu přidruženého k zadanému ID funkce.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="cf1a3-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-104">This method is obsolete.</span></span> <span data-ttu-id="cf1a3-105">Místo toho použijte metodu [ICorProfilerInfo2:: GetCodeInfo2 –](icorprofilerinfo2-getcodeinfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cf1a3-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf1a3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf1a3-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf1a3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf1a3-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cf1a3-108">pro ID funkce, ke které je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="cf1a3-109">mimo Ukazatel na pole bajtů, které tvoří nativní kód funkce.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="cf1a3-110">mimo Ukazatel na celé číslo, které určuje velikost (v bajtech) nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf1a3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf1a3-111">Remarks</span></span>  
 <span data-ttu-id="cf1a3-112">Za účelem optimalizace výkonu je modul runtime ve .NET Framework verze 2,0 rozdělen do více oblastí předkompilovaným nativním kódem funkce.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="cf1a3-113">V důsledku toho `GetCodeInfo` je metoda v .NET Framework 2,0 zastaralá, protože není schopna zpracovat rozsah nativního kódu funkce.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="cf1a3-114">Profilery by se měly místo toho přepnout na použití obecnější `ICorProfilerInfo2::GetCodeInfo2` metody.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="cf1a3-115">Tato funkce používá vyrovnávací paměti přidělené volajícím.</span><span class="sxs-lookup"><span data-stu-id="cf1a3-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf1a3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf1a3-116">Requirements</span></span>  
 <span data-ttu-id="cf1a3-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf1a3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf1a3-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cf1a3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf1a3-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf1a3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf1a3-120">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="cf1a3-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf1a3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf1a3-121">See also</span></span>

- [<span data-ttu-id="cf1a3-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf1a3-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cf1a3-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="cf1a3-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cf1a3-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="cf1a3-124">Profiling</span></span>](index.md)
