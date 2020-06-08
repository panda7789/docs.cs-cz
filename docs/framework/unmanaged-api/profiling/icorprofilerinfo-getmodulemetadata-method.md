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
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502948"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="06aac-102">ICorProfilerInfo::GetModuleMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="06aac-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="06aac-103">Získá instanci rozhraní metadat, která se mapuje na určený modul.</span><span class="sxs-lookup"><span data-stu-id="06aac-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06aac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06aac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06aac-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06aac-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="06aac-106">pro ID modulu, ke kterému bude namapována instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06aac-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="06aac-107">pro Hodnota výčtu [CorOpenFlags –](../metadata/coropenflags-enumeration.md) , která určuje režim otevírání souborů manifestu.</span><span class="sxs-lookup"><span data-stu-id="06aac-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="06aac-108">`ofRead` `ofWrite` `ofNoTransform` Platné jsou pouze bity a bitů.</span><span class="sxs-lookup"><span data-stu-id="06aac-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="06aac-109">pro Referenční identifikátor (GUID) rozhraní metadat, jehož instance bude načtena.</span><span class="sxs-lookup"><span data-stu-id="06aac-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="06aac-110">Seznam rozhraní naleznete v tématu [rozhraní metadat](../metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="06aac-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="06aac-111">mimo Ukazatel na adresu instance rozhraní metadat.</span><span class="sxs-lookup"><span data-stu-id="06aac-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06aac-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06aac-112">Remarks</span></span>  
 <span data-ttu-id="06aac-113">Můžete požádat, aby se metadata otevírala v režimu pro čtení i zápis, ale výsledkem bude pomalejší spuštění tohoto programu, protože změny v metadatech nejdou optimalizovat, protože byly z kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="06aac-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="06aac-114">Některé moduly (například moduly prostředků) nemají žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="06aac-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="06aac-115">V těchto případech `GetModuleMetaData` vrátí hodnotu HRESULT S_FALSE a hodnotu null v \* `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="06aac-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06aac-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06aac-116">Requirements</span></span>  
 <span data-ttu-id="06aac-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06aac-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06aac-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="06aac-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06aac-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06aac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06aac-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06aac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06aac-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06aac-121">See also</span></span>

- [<span data-ttu-id="06aac-122">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06aac-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
