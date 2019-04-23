---
title: ICorProfilerInfo3::GetRuntimeInformation – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164928"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="65cb9-102">ICorProfilerInfo3::GetRuntimeInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="65cb9-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="65cb9-103">Poskytuje informace o verzi o common language runtime (CLR), která je právě profilována.</span><span class="sxs-lookup"><span data-stu-id="65cb9-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65cb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65cb9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="65cb9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65cb9-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="65cb9-106">[out] Identifikátor zástupce spuštěné instance modulu CLR v procesu.</span><span class="sxs-lookup"><span data-stu-id="65cb9-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="65cb9-107">To je stejný jako `ClrInstanceID` , že sestavy trasování událostí pro Windows (ETW) spouštěcí událost.</span><span class="sxs-lookup"><span data-stu-id="65cb9-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="65cb9-108">[out] Typ modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="65cb9-108">[out] The runtime type.</span></span> <span data-ttu-id="65cb9-109">Tento parametr vrátí `COR_PRF_DESKTOP_CLR` pro desktopovou verzi modulu CLR, nebo `COR_PRF_CORE_CLR` základní verze CLR použít v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="65cb9-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="65cb9-110">[out] Číslo hlavní verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="65cb9-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="65cb9-111">[out] Číslo podverze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="65cb9-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="65cb9-112">[out] Číslo verze sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="65cb9-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="65cb9-113">[out] Číslo verze modulu CLR, který je přiřazen k aktualizaci softwaru.</span><span class="sxs-lookup"><span data-stu-id="65cb9-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="65cb9-114">[in] Délka ve znacích, vyrovnávací paměti, která `szVersionString` odkazuje na.</span><span class="sxs-lookup"><span data-stu-id="65cb9-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="65cb9-115">[out] Délka ve znacích, z `szVersionString`.</span><span class="sxs-lookup"><span data-stu-id="65cb9-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="65cb9-116">[out] Řetězec verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="65cb9-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65cb9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65cb9-117">Remarks</span></span>  
 <span data-ttu-id="65cb9-118">Můžete předat hodnotu null pro žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="65cb9-118">You may pass null for any parameter.</span></span> <span data-ttu-id="65cb9-119">Ale `pcchVersionString` nemůže být null. Pokud `szVersionString` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="65cb9-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65cb9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65cb9-120">Requirements</span></span>  
 <span data-ttu-id="65cb9-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65cb9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65cb9-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65cb9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65cb9-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65cb9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65cb9-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65cb9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65cb9-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65cb9-125">See also</span></span>

- [<span data-ttu-id="65cb9-126">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65cb9-126">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="65cb9-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="65cb9-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="65cb9-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="65cb9-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
