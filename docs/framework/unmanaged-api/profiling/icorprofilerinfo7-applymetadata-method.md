---
title: ICorProfilerInfo7::ApplyMetaData Method
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aff6f63bb9f41fe45b22854787667070929bf987
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213763"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="24511-102">ICorProfilerInfo7::ApplyMetaData Method</span><span class="sxs-lookup"><span data-stu-id="24511-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="24511-103">[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="24511-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="24511-104">Metadata nově definované se vztahuje `IMetadataEmit::Define*` metody pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="24511-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24511-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24511-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24511-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="24511-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="24511-107">[in] Identifikátor modulu, jehož metadat byl změněn.</span><span class="sxs-lookup"><span data-stu-id="24511-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24511-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24511-108">Remarks</span></span>  
 <span data-ttu-id="24511-109">Pokud dojde ke změně metadat po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětné volání, musí volat tuto metodu před použitím novými metadaty.</span><span class="sxs-lookup"><span data-stu-id="24511-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="24511-110">`ApplyMetaData` podporuje pouze přidávání následující typy metadat:</span><span class="sxs-lookup"><span data-stu-id="24511-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="24511-111">`AssemblyRef` záznamy, které vytvoříte pomocí volání [imetadataassemblyemit::defineassemblyref –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="24511-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="24511-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="24511-112">method.</span></span>  
  
-   <span data-ttu-id="24511-113">`TypeRef` záznamy, které vytvoříte pomocí volání [imetadataemit::definetyperefbyname –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="24511-114">`TypeSpec` záznamy, které vytvoříte pomocí volání [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="24511-115">`MemberRef` záznamy, které vytvoříte pomocí volání [imetadataemit::definememberref –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="24511-116">`MemberSpec` záznamy, které vytvoříte pomocí volání [imetadataemit2::definemethodspec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="24511-117">`UserString` záznamy, které vytvoříte pomocí volání [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="24511-118">Od verze .NET Core 3.0, `ApplyMetaData` také podporuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="24511-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="24511-119">`TypeDef` záznamy, které vytvoříte pomocí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="24511-120">`MethodDef` záznamy, které vytvoříte pomocí volání [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="24511-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="24511-121">Ale přidávání virtuální metody k existujícímu typu se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="24511-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="24511-122">Virtuální metody, je třeba přidat před [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="24511-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="24511-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24511-123">Requirements</span></span>  
 <span data-ttu-id="24511-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24511-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24511-125">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24511-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24511-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24511-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24511-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24511-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24511-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24511-128">See also</span></span>

- [<span data-ttu-id="24511-129">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24511-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
