---
title: "ICorProfilerInfo3::GetRuntimeInformation – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5eadd9970d29cc65d8411692407dcae5471e51c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="63eb4-102">ICorProfilerInfo3::GetRuntimeInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="63eb4-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="63eb4-103">Poskytuje informace o verzi o common language runtime (CLR), který je profilovaný.</span><span class="sxs-lookup"><span data-stu-id="63eb4-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63eb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63eb4-104">Syntax</span></span>  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63eb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63eb4-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="63eb4-106">[out] ID zástupce spuštěné instance CLR v procesu.</span><span class="sxs-lookup"><span data-stu-id="63eb4-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="63eb4-107">Je to stejné jako `ClrInstanceID` , sestavy trasování událostí pro událost spuštění systému Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="63eb4-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="63eb4-108">[out] Typ modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="63eb4-108">[out] The runtime type.</span></span> <span data-ttu-id="63eb4-109">Tento parametr vrátí `COR_PRF_DESKTOP_CLR` pro plochy verzi modulu CLR, nebo `COR_PRF_CORE_CLR` pro základní verzi modulu CLR použít v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="63eb4-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="63eb4-110">[out] Hlavní číslo verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="63eb4-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="63eb4-111">[out] Číslo podverze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="63eb4-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="63eb4-112">[out] Číslo verze sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="63eb4-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="63eb4-113">[out] Číslo verze modulu CLR, který je přidružen aktualizace softwaru.</span><span class="sxs-lookup"><span data-stu-id="63eb4-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="63eb4-114">[v] Délka ve znacích vyrovnávací paměti, `szVersionString` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="63eb4-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="63eb4-115">[out] Délka ve znacích, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="63eb4-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="63eb4-116">[out] Řetězec verze CLR.</span><span class="sxs-lookup"><span data-stu-id="63eb4-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63eb4-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="63eb4-117">Remarks</span></span>  
 <span data-ttu-id="63eb4-118">Vám může předat hodnotu null pro libovolný parametr.</span><span class="sxs-lookup"><span data-stu-id="63eb4-118">You may pass null for any parameter.</span></span> <span data-ttu-id="63eb4-119">Ale `pcchVersionString` nemůže být null. Pokud `szVersionString` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="63eb4-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63eb4-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="63eb4-120">Requirements</span></span>  
 <span data-ttu-id="63eb4-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63eb4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63eb4-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63eb4-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63eb4-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63eb4-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63eb4-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63eb4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63eb4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="63eb4-125">See Also</span></span>  
 [<span data-ttu-id="63eb4-126">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="63eb4-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="63eb4-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="63eb4-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="63eb4-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="63eb4-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
