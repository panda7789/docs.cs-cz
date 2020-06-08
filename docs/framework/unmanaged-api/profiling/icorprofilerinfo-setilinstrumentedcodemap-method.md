---
title: ICorProfilerInfo::SetILInstrumentedCodeMap – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: cac8e9570dab55af6b6e1fcf6f53b6a697727972
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502909"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="a65be-102">ICorProfilerInfo::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="a65be-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="a65be-103">Nastaví mapu kódu pro určenou funkci pomocí zadaných položek mapování jazyka MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="a65be-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="a65be-104">V .NET Framework verze 2,0 `SetILInstrumentedCodeMap` bude volání na `FunctionID` , které představuje obecnou funkci v konkrétní doméně aplikace, ovlivnit všechny instance této funkce v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="a65be-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="a65be-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a65be-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="a65be-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a65be-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="a65be-107">pro ID funkce, pro kterou chcete nastavit mapu kódu.</span><span class="sxs-lookup"><span data-stu-id="a65be-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="a65be-108">pro Logická hodnota, která označuje, zda `SetILInstrumentedCodeMap` je volání metody prvním pro konkrétní `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="a65be-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="a65be-109">Nastavte `fStartJit` na `true` při prvním volání na `SetILInstrumentedCodeMap` pro daný `FunctionID` a `false` potom na.</span><span class="sxs-lookup"><span data-stu-id="a65be-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="a65be-110">pro Počet prvků v `cILMapEntries` poli.</span><span class="sxs-lookup"><span data-stu-id="a65be-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="a65be-111">pro Pole struktur COR_IL_MAP, z nichž každý Určuje posun MSIL.</span><span class="sxs-lookup"><span data-stu-id="a65be-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="a65be-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a65be-112">Remarks</span></span>

<span data-ttu-id="a65be-113">Profiler často vkládá příkazy v rámci zdrojového kódu metody pro instrumentaci této metody (například pro oznámení, když je dosaženo daného řádku zdroje).</span><span class="sxs-lookup"><span data-stu-id="a65be-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="a65be-114">`SetILInstrumentedCodeMap`umožňuje profileru mapovat původní instrukce jazyka MSIL na jejich nová umístění.</span><span class="sxs-lookup"><span data-stu-id="a65be-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="a65be-115">Profiler může pomocí metody [ICorProfilerInfo:: GetILToNativeMapping –](icorprofilerinfo-getiltonativemapping-method.md) získat původní posun MSIL pro daný nativní posun.</span><span class="sxs-lookup"><span data-stu-id="a65be-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="a65be-116">Ladicí program předpokládá, že každý starý posun odkazuje na posun MSIL v rámci původního, neupraveného kódu MSIL a že každý nový posun odkazuje na posun MSIL v rámci nového, instrumentované kódu.</span><span class="sxs-lookup"><span data-stu-id="a65be-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="a65be-117">Mapa by se měla seřadit ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a65be-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="a65be-118">Chcete-li, aby krokování fungovalo správně, postupujte podle těchto pokynů:</span><span class="sxs-lookup"><span data-stu-id="a65be-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="a65be-119">Neměňte pořadí načítacího kódu MSIL.</span><span class="sxs-lookup"><span data-stu-id="a65be-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="a65be-120">Neodstraňujte původní kód MSIL.</span><span class="sxs-lookup"><span data-stu-id="a65be-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="a65be-121">Zahrnout položky pro všechny body sekvence ze souboru databáze programu (PDB) na mapě.</span><span class="sxs-lookup"><span data-stu-id="a65be-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="a65be-122">Mapa neinterpoluje chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="a65be-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="a65be-123">Proto s ohledem na následující mapu:</span><span class="sxs-lookup"><span data-stu-id="a65be-123">So, given the following map:</span></span>

  <span data-ttu-id="a65be-124">(0 Old, 0 novinek)</span><span class="sxs-lookup"><span data-stu-id="a65be-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="a65be-125">(5 Old, 10 nových)</span><span class="sxs-lookup"><span data-stu-id="a65be-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="a65be-126">(9 Old, 20 novinek)</span><span class="sxs-lookup"><span data-stu-id="a65be-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="a65be-127">Starý posun 0, 1, 2, 3 nebo 4 se namapuje na nový posun 0.</span><span class="sxs-lookup"><span data-stu-id="a65be-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="a65be-128">Starý posun z 5, 6, 7 nebo 8 se namapuje na nový posun 10.</span><span class="sxs-lookup"><span data-stu-id="a65be-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="a65be-129">Původní posun 9 nebo vyšší se namapuje na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="a65be-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="a65be-130">Nové odsazení 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 bude namapováno na starý posun 0.</span><span class="sxs-lookup"><span data-stu-id="a65be-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="a65be-131">Nové posuny 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou namapovány na starý posun 5.</span><span class="sxs-lookup"><span data-stu-id="a65be-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="a65be-132">Nový posun o hodnotě 20 nebo vyšší bude mapován na starý posun 9.</span><span class="sxs-lookup"><span data-stu-id="a65be-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="a65be-133">V .NET Framework 3,5 a předchozích verzích přidělíte `rgILMapEntries` pole voláním metody [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) .</span><span class="sxs-lookup"><span data-stu-id="a65be-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="a65be-134">Vzhledem k tomu, že modul runtime převezme vlastnictví této paměti, Profiler by se neměl pokoušet o uvolnění.</span><span class="sxs-lookup"><span data-stu-id="a65be-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="a65be-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a65be-135">Requirements</span></span>

<span data-ttu-id="a65be-136">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a65be-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a65be-137">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a65be-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a65be-138">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a65be-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a65be-139">**Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65be-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a65be-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a65be-140">See also</span></span>

- [<span data-ttu-id="a65be-141">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a65be-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
