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
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868548"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="11dc2-102">ICorProfilerInfo3::GetRuntimeInformation – metoda</span><span class="sxs-lookup"><span data-stu-id="11dc2-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="11dc2-103">Poskytuje informace o verzi modulu CLR (Common Language Runtime), který je profilace.</span><span class="sxs-lookup"><span data-stu-id="11dc2-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11dc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11dc2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="11dc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11dc2-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="11dc2-106">mimo ID zástupce běžící instance CLR v procesu.</span><span class="sxs-lookup"><span data-stu-id="11dc2-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="11dc2-107">To je totéž jako `ClrInstanceID`, které sestavy událostí při spuštění trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="11dc2-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="11dc2-108">mimo Typ modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="11dc2-108">[out] The runtime type.</span></span> <span data-ttu-id="11dc2-109">Tento parametr vrátí `COR_PRF_DESKTOP_CLR` verze modulu CLR pro plochu nebo `COR_PRF_CORE_CLR` základní verzi CLR použitou v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="11dc2-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="11dc2-110">mimo Hlavní číslo verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="11dc2-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="11dc2-111">mimo Číslo dílčí verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="11dc2-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="11dc2-112">mimo Číslo verze buildu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="11dc2-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="11dc2-113">mimo Číslo verze modulu CLR, který je spojen s aktualizací softwaru.</span><span class="sxs-lookup"><span data-stu-id="11dc2-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="11dc2-114">pro Délka vyrovnávací paměti v znacích, na kterou `szVersionString` odkazuje.</span><span class="sxs-lookup"><span data-stu-id="11dc2-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="11dc2-115">mimo Délka `szVersionString`znaků.</span><span class="sxs-lookup"><span data-stu-id="11dc2-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="11dc2-116">mimo Řetězec verze CLR.</span><span class="sxs-lookup"><span data-stu-id="11dc2-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11dc2-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11dc2-117">Remarks</span></span>  
 <span data-ttu-id="11dc2-118">Pro libovolný parametr můžete předat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="11dc2-118">You may pass null for any parameter.</span></span> <span data-ttu-id="11dc2-119">`pcchVersionString` však nesmí mít hodnotu null, pokud `szVersionString` není také null.</span><span class="sxs-lookup"><span data-stu-id="11dc2-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11dc2-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11dc2-120">Requirements</span></span>  
 <span data-ttu-id="11dc2-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11dc2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11dc2-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11dc2-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11dc2-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11dc2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11dc2-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11dc2-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11dc2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11dc2-125">See also</span></span>

- [<span data-ttu-id="11dc2-126">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11dc2-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="11dc2-127">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="11dc2-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11dc2-128">Profilace</span><span class="sxs-lookup"><span data-stu-id="11dc2-128">Profiling</span></span>](index.md)
