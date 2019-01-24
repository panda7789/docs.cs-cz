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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1663a36ab36980af709a861b3fb0666be6fecdfb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607472"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="8ff91-102">ICorProfilerInfo::GetModuleMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="8ff91-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="8ff91-103">Získá instanci rozhraní metadat, který se mapuje na zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="8ff91-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ff91-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ff91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ff91-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8ff91-106">[in] ID modulu, ke které se namapují instanci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8ff91-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="8ff91-107">[in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčet, který určuje režim pro otevření souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="8ff91-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="8ff91-108">Pouze `ofRead`, `ofWrite` a `ofNoTransform` bity jsou platné.</span><span class="sxs-lookup"><span data-stu-id="8ff91-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="8ff91-109">[in] Odkaz na Identifikátor (GUID) metadat rozhraní, jejichž instance se byla načtena.</span><span class="sxs-lookup"><span data-stu-id="8ff91-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="8ff91-110">Zobrazit [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) seznam rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8ff91-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="8ff91-111">[out] Ukazatel na adresu rozhraní instance metadat.</span><span class="sxs-lookup"><span data-stu-id="8ff91-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ff91-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ff91-112">Remarks</span></span>  
 <span data-ttu-id="8ff91-113">Požádat o metadat, která chcete otevřít v režimu čtení a zápisu, ale to způsobí pomalejší metadat provádění programu, protože změny provedené metadata nelze optimalizovaná, jako kdyby byly z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8ff91-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="8ff91-114">Některé moduly (například moduly prostředků) mají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="8ff91-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="8ff91-115">V takových případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a s hodnotou null v \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="8ff91-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ff91-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ff91-116">Requirements</span></span>  
 <span data-ttu-id="8ff91-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ff91-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ff91-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ff91-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ff91-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ff91-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ff91-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ff91-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff91-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ff91-121">See also</span></span>
- [<span data-ttu-id="8ff91-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ff91-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
