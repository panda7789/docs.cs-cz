---
title: "ICorProfilerInfo7::ApplyMetaData – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e79d687d3d777895dea9427e4865c2fc866f50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="72871-102">ICorProfilerInfo7::ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="72871-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="72871-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="72871-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="72871-104">Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="72871-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72871-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72871-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72871-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="72871-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="72871-107">[v] Identifikátor modulu, jehož metadata byl změněn.</span><span class="sxs-lookup"><span data-stu-id="72871-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72871-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72871-108">Remarks</span></span>  
 <span data-ttu-id="72871-109">Pokud po provedení změn metadat [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětné volání, musí volat tuto metodu před použitím novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="72871-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="72871-110">`ApplyMetaData`podporuje se jenom přidávání následující typy metadat:</span><span class="sxs-lookup"><span data-stu-id="72871-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="72871-111">`AssemblyRef`záznamy, které vytvoříte pomocí volání [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="72871-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="72871-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-112">method.</span></span>  
  
-   <span data-ttu-id="72871-113">`TypeRef`záznamy, které vytvoříte pomocí volání [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="72871-114">`TypeSpec`záznamy, které vytvoříte pomocí volání [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="72871-115">`MemberRef`záznamy, které vytvoříte pomocí volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="72871-116">`MemberSpec`záznamy, které vytvoříte pomocí volání [imetadataemit2::definemethodspec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="72871-117">`UserString`záznamy, které vytvoříte pomocí volání [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="72871-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72871-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72871-118">Requirements</span></span>  
 <span data-ttu-id="72871-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72871-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72871-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72871-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72871-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72871-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72871-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72871-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72871-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="72871-123">See Also</span></span>  
 [<span data-ttu-id="72871-124">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72871-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
