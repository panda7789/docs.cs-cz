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
ms.openlocfilehash: b8e503af11fa1d02aac2ec83edde0ffbd562d8e5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496396"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="94852-102">ICorProfilerInfo3::GetRuntimeInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="94852-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="94852-103">Poskytuje informace o verzi modulu CLR (Common Language Runtime), který je profilace.</span><span class="sxs-lookup"><span data-stu-id="94852-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94852-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94852-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="94852-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94852-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="94852-106">mimo ID zástupce běžící instance CLR v procesu.</span><span class="sxs-lookup"><span data-stu-id="94852-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="94852-107">To je stejné jako u `ClrInstanceID` sestav událostí spuštění trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="94852-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="94852-108">mimo Typ modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="94852-108">[out] The runtime type.</span></span> <span data-ttu-id="94852-109">Tento parametr vrátí hodnotu `COR_PRF_DESKTOP_CLR` pro desktopovou verzi CLR nebo `COR_PRF_CORE_CLR` základní verzi CLR použitou v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="94852-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="94852-110">mimo Hlavní číslo verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="94852-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="94852-111">mimo Číslo dílčí verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="94852-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="94852-112">mimo Číslo verze buildu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="94852-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="94852-113">mimo Číslo verze modulu CLR, který je spojen s aktualizací softwaru.</span><span class="sxs-lookup"><span data-stu-id="94852-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="94852-114">pro Délka vyrovnávací paměti v znacích, `szVersionString` na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="94852-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="94852-115">mimo Délka v znacích `szVersionString` .</span><span class="sxs-lookup"><span data-stu-id="94852-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="94852-116">mimo Řetězec verze CLR.</span><span class="sxs-lookup"><span data-stu-id="94852-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94852-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94852-117">Remarks</span></span>  
 <span data-ttu-id="94852-118">Pro libovolný parametr můžete předat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="94852-118">You may pass null for any parameter.</span></span> <span data-ttu-id="94852-119">Nicméně `pcchVersionString` nemůže mít hodnotu null, pokud `szVersionString` není také null.</span><span class="sxs-lookup"><span data-stu-id="94852-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94852-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94852-120">Requirements</span></span>  
 <span data-ttu-id="94852-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94852-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94852-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="94852-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94852-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="94852-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94852-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94852-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94852-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94852-125">See also</span></span>

- [<span data-ttu-id="94852-126">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="94852-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="94852-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="94852-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="94852-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="94852-128">Profiling</span></span>](index.md)
