---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILInstrumentedCodeMap
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 127f6d76e85ed30f1407d16f8d81c93dd2941960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="8ce13-102">ICorProfilerInfo::SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="8ce13-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="8ce13-103">Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapy (MSIL intermediate language) společnosti Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8ce13-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce13-104">V rozhraní .NET Framework verze 2.0, volání `SetILInstrumentedCodeMap` na `FunctionID` , představuje obecný fungovat v určité domény aplikace bude mít vliv na všechny instance této funkce v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ce13-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce13-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ce13-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ce13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ce13-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8ce13-107">[v] ID funkce, pro kterou chcete nastavit Mapa kódu.</span><span class="sxs-lookup"><span data-stu-id="8ce13-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="8ce13-108">[v] Logická hodnota, která určuje, zda volání `SetILInstrumentedCodeMap` metoda je první pro konkrétní `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="8ce13-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="8ce13-109">Nastavit `fStartJit` k `true` v prvním volání `SetILInstrumentedCodeMap` pro danou `FunctionID`a `false` po tomto datu.</span><span class="sxs-lookup"><span data-stu-id="8ce13-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="8ce13-110">[v] Počet elementů ve `cILMapEntries` pole.</span><span class="sxs-lookup"><span data-stu-id="8ce13-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="8ce13-111">[v] Pole cor_il_map – struktury, z nichž každý určuje posun MSIL.</span><span class="sxs-lookup"><span data-stu-id="8ce13-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce13-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ce13-112">Remarks</span></span>  
 <span data-ttu-id="8ce13-113">Profileru často vloží příkazů v rámci zdrojový kód metody za účelem instrumentace dané metody (například upozornit, když je dosaženo zadaná zdrojová řádku).</span><span class="sxs-lookup"><span data-stu-id="8ce13-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="8ce13-114">`SetILInstrumentedCodeMap`Umožňuje profileru mapovat původní pokynů MSIL do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="8ce13-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="8ce13-115">Můžete použít profileru [icorprofilerinfo::getiltonativemapping –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metoda získat původní MSIL posunutí pro daný nativní posun.</span><span class="sxs-lookup"><span data-stu-id="8ce13-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="8ce13-116">Ladicí program bude předpokládat, že každý staré posun odkazuje na MSIL posun v rámci kód MSIL původní, beze změny a že každý nový posun odkazuje na MSIL posun v rámci kód nové, instrumentovaného.</span><span class="sxs-lookup"><span data-stu-id="8ce13-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="8ce13-117">Mapy by měly být seřazeny ve vzestupném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8ce13-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="8ce13-118">Pro krokování s fungovalo správně, postupujte podle následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="8ce13-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="8ce13-119">Není uspořádat instrumentovaného MSIL kód.</span><span class="sxs-lookup"><span data-stu-id="8ce13-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="8ce13-120">Neodebírejte původní MSIL kód.</span><span class="sxs-lookup"><span data-stu-id="8ce13-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="8ce13-121">Zahrnete položky pro všechny body sekvence ze souboru databáze (PDB) program v mapě.</span><span class="sxs-lookup"><span data-stu-id="8ce13-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="8ce13-122">Mapy není interpolovat položky.</span><span class="sxs-lookup"><span data-stu-id="8ce13-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="8ce13-123">Ano danou následující mapa:</span><span class="sxs-lookup"><span data-stu-id="8ce13-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="8ce13-124">(0 starý, 0 nové)</span><span class="sxs-lookup"><span data-stu-id="8ce13-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="8ce13-125">(5 starý, 10 nové)</span><span class="sxs-lookup"><span data-stu-id="8ce13-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="8ce13-126">(9 starý, 20 nové)</span><span class="sxs-lookup"><span data-stu-id="8ce13-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="8ce13-127">Původní posun 0, 1, 2, 3 nebo 4 budou mapována na nový posunu 0.</span><span class="sxs-lookup"><span data-stu-id="8ce13-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="8ce13-128">Původní posun 5, 6, 7 nebo 8 budou mapována na nový posun 10.</span><span class="sxs-lookup"><span data-stu-id="8ce13-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="8ce13-129">Původní posun 9 nebo vyšší budou mapována na nový posun 20.</span><span class="sxs-lookup"><span data-stu-id="8ce13-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="8ce13-130">Nové posun 0, 1, 2, 3, 4, 5, 6, 7, 8 nebo 9 budou mapována na staré posunu 0.</span><span class="sxs-lookup"><span data-stu-id="8ce13-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="8ce13-131">Nové posun 10, 11, 12, 13, 14, 15, 16, 17, 18 nebo 19 budou mapována na staré posun 5.</span><span class="sxs-lookup"><span data-stu-id="8ce13-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="8ce13-132">Nové posun 20 nebo vyšší budou mapována na staré posun 9.</span><span class="sxs-lookup"><span data-stu-id="8ce13-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce13-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ce13-133">Requirements</span></span>  
 <span data-ttu-id="8ce13-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ce13-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce13-135">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ce13-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ce13-136">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce13-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce13-137">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce13-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce13-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ce13-138">See Also</span></span>  
 [<span data-ttu-id="8ce13-139">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ce13-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
