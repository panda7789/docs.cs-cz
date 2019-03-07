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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e96a84f9dc96b2eb508034d5277902ff3f328c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490083"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="e0a2c-102">ICorProfilerInfo::GetCodeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e0a2c-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="e0a2c-103">Vrátí rozsah nativního kódu přidružené k ID zadanou funkci.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="e0a2c-104">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-104">This method is obsolete.</span></span> <span data-ttu-id="e0a2c-105">Použití [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a2c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0a2c-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0a2c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a2c-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e0a2c-108">[in] ID funkce, ke kterému je přidružen nativní kód.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="e0a2c-109">[out] Ukazatel na pole bajtů, které tvoří nativního kódu funkce.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="e0a2c-110">[out] Ukazatel na celé číslo, které určuje velikost v bajtech nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0a2c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0a2c-111">Remarks</span></span>  
 <span data-ttu-id="e0a2c-112">Za účelem optimalizace výkonu modulu runtime v rozhraní .NET Framework verze 2.0 rozdělí předkompilované nativního kódu funkce do několika oblastí.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="e0a2c-113">V důsledku toho `GetCodeInfo` metoda je zastaralé v rozhraní .NET Framework 2.0, protože není schopen zpracovat rozsah nativního kódu funkce.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="e0a2c-114">Profilovací programy by měl přepnout na použití obecnější `ICorProfilerInfo2::GetCodeInfo2` metoda místo.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="e0a2c-115">Tato funkce využívá volající – přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e0a2c-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a2c-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0a2c-116">Requirements</span></span>  
 <span data-ttu-id="e0a2c-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a2c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a2c-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0a2c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0a2c-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0a2c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0a2c-120">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="e0a2c-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a2c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0a2c-121">See also</span></span>
- [<span data-ttu-id="e0a2c-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0a2c-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e0a2c-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e0a2c-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="e0a2c-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="e0a2c-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
