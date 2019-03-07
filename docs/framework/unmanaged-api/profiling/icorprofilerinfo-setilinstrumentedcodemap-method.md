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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc13dc1348a6d397c86b03976c86c3595f749cf6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480062"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="c772c-102">ICorProfilerInfo::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="c772c-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="c772c-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="c772c-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c772c-104">V rozhraní .NET Framework verze 2.0, volání `SetILInstrumentedCodeMap` na `FunctionID` , představuje obecnou funkci v určité domény aplikace bude mít vliv na všechny instance této funkce v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c772c-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c772c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c772c-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c772c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c772c-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c772c-107">[in] ID funkce, pro kterou chcete nastavit mapu kódu.</span><span class="sxs-lookup"><span data-stu-id="c772c-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="c772c-108">[in] Logická hodnota, která určuje, zda volání `SetILInstrumentedCodeMap` metody je první pro konkrétní `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="c772c-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="c772c-109">Nastavit `fStartJit` k `true` v prvním volání `SetILInstrumentedCodeMap` pro dané `FunctionID`a získat `false` po tomto datu.</span><span class="sxs-lookup"><span data-stu-id="c772c-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="c772c-110">[in] Počet prvků v `cILMapEntries` pole.</span><span class="sxs-lookup"><span data-stu-id="c772c-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="c772c-111">[in] Pole struktur cor_il_map –, z nichž každý Určuje prodlevu jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="c772c-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c772c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c772c-112">Remarks</span></span>  
 <span data-ttu-id="c772c-113">Profiler často vloží příkazy ve zdrojovém kódu metody k instrumentaci metody (například upozornit, když je dosaženo dané zdrojový řádek).</span><span class="sxs-lookup"><span data-stu-id="c772c-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="c772c-114">`SetILInstrumentedCodeMap` Umožňuje profileru mapování původní instrukce jazyka MSIL do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="c772c-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="c772c-115">Profiler může použít [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metodu k získání původní posun jazyka MSIL pro danou nativní posun.</span><span class="sxs-lookup"><span data-stu-id="c772c-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="c772c-116">Ladicí program bude předpokládat, že každý staré posun odkazuje na jazyka MSIL posun v rámci původní verzí bez úprav kódu MSIL a, že každý nový posun odkazuje na MSIL posun v rámci nové instrumentované kódu.</span><span class="sxs-lookup"><span data-stu-id="c772c-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="c772c-117">Na mapě by měly být seřazeny vzestupně v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c772c-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="c772c-118">Pro krokování fungovalo správně, postupujte podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="c772c-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="c772c-119">Nemění pořadí instrumentované kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="c772c-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="c772c-120">Neodebírejte původní kód jazyka MSIL.</span><span class="sxs-lookup"><span data-stu-id="c772c-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="c772c-121">Zahrnete položky pro všechny body posloupnosti ze souboru databáze (PDB) programu na mapě.</span><span class="sxs-lookup"><span data-stu-id="c772c-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="c772c-122">Mapa není interpolovat chybějící položky.</span><span class="sxs-lookup"><span data-stu-id="c772c-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="c772c-123">Ano uvedené následující mapování:</span><span class="sxs-lookup"><span data-stu-id="c772c-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="c772c-124">(0 staré, 0 nové)</span><span class="sxs-lookup"><span data-stu-id="c772c-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="c772c-125">(5 staré, 10 nové)</span><span class="sxs-lookup"><span data-stu-id="c772c-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="c772c-126">(9 staré, 20 nové)</span><span class="sxs-lookup"><span data-stu-id="c772c-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="c772c-127">Staré posun 0, 1, 2, 3 nebo 4 se namapují na nové posun 0.</span><span class="sxs-lookup"><span data-stu-id="c772c-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="c772c-128">Posun staré 5, 6, 7 nebo 8 se namapují na nové posun 10.</span><span class="sxs-lookup"><span data-stu-id="c772c-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="c772c-129">Staré posun 9 nebo vyšší se namapují na nové posun 20.</span><span class="sxs-lookup"><span data-stu-id="c772c-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="c772c-130">Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 a 9 se namapují na staré posun 0.</span><span class="sxs-lookup"><span data-stu-id="c772c-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="c772c-131">Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 se namapují na staré posun 5.</span><span class="sxs-lookup"><span data-stu-id="c772c-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="c772c-132">Nové posun 20 nebo vyšší se namapují na staré posun 9.</span><span class="sxs-lookup"><span data-stu-id="c772c-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c772c-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c772c-133">Requirements</span></span>  
 <span data-ttu-id="c772c-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c772c-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c772c-135">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c772c-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c772c-136">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c772c-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c772c-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c772c-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c772c-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c772c-138">See also</span></span>
- [<span data-ttu-id="c772c-139">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c772c-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
