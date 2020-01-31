---
title: ICorProfilerInfo::GetModuleMetaData – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: 6e787de6287dc5b3091d3671d3da2f2154b12e88
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869921"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="4df8f-102">ICorProfilerInfo::GetModuleMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="4df8f-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="4df8f-103">Získá instanci rozhraní metadat, která se mapuje na určený modul.</span><span class="sxs-lookup"><span data-stu-id="4df8f-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4df8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4df8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4df8f-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4df8f-106">pro ID modulu, ke kterému bude namapována instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4df8f-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4df8f-107">pro Hodnota výčtu [CorOpenFlags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) , která určuje režim otevírání souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="4df8f-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="4df8f-108">Platné jsou pouze bity `ofRead`, `ofWrite` a `ofNoTransform`.</span><span class="sxs-lookup"><span data-stu-id="4df8f-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="4df8f-109">pro Referenční identifikátor (GUID) rozhraní metadat, jehož instance bude načtena.</span><span class="sxs-lookup"><span data-stu-id="4df8f-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="4df8f-110">Seznam rozhraní naleznete v tématu [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="4df8f-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="4df8f-111">mimo Ukazatel na adresu instance rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="4df8f-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4df8f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4df8f-112">Remarks</span></span>  
 <span data-ttu-id="4df8f-113">Můžete požádat, aby se metadata otevírala v režimu pro čtení i zápis, ale výsledkem bude pomalejší spuštění tohoto programu, protože změny v metadatech nejdou optimalizovat, protože byly z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="4df8f-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="4df8f-114">Některé moduly (například moduly prostředků) nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="4df8f-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="4df8f-115">V těchto případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a hodnotu null v hodnotě \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="4df8f-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4df8f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4df8f-116">Requirements</span></span>  
 <span data-ttu-id="4df8f-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4df8f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4df8f-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4df8f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4df8f-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4df8f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4df8f-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4df8f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df8f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4df8f-121">See also</span></span>

- [<span data-ttu-id="4df8f-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4df8f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
