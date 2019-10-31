---
title: 'ICorProfilerInfo7:: ApplyMetaData – metoda'
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
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130354"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="865a4-102">ICorProfilerInfo7:: ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="865a4-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="865a4-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="865a4-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="865a4-104">Aplikuje metadata nově definovaná metodami `IMetadataEmit::Define*` do zadaného modulu.</span><span class="sxs-lookup"><span data-stu-id="865a4-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865a4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="865a4-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="865a4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="865a4-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="865a4-107">pro Identifikátor modulu, jehož metadata se změnila.</span><span class="sxs-lookup"><span data-stu-id="865a4-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="865a4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="865a4-108">Remarks</span></span>  
 <span data-ttu-id="865a4-109">Pokud jsou změny metadat provedeny po zpětném volání [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) , je nutné před použitím nových metadat zavolat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="865a4-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="865a4-110">`ApplyMetaData` podporuje pouze přidávání následujících typů metadat:</span><span class="sxs-lookup"><span data-stu-id="865a4-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="865a4-111">`AssemblyRef` záznamy, které vytvoříte voláním metody [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="865a4-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="865a4-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="865a4-112">method.</span></span>  
  
- <span data-ttu-id="865a4-113">`TypeRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="865a4-114">`TypeSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit:: gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="865a4-115">`MemberRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="865a4-116">`MemberSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="865a4-117">`UserString` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="865a4-118">Počínaje rozhraním .NET Core 3,0 `ApplyMetaData` také podporuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="865a4-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="865a4-119">`TypeDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="865a4-120">`MethodDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="865a4-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="865a4-121">Přidání virtuálních metod do existujícího typu však není podporováno.</span><span class="sxs-lookup"><span data-stu-id="865a4-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="865a4-122">Před zpětným voláním [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) musí být virtuální metody přidané.</span><span class="sxs-lookup"><span data-stu-id="865a4-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="865a4-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="865a4-123">Requirements</span></span>  
 <span data-ttu-id="865a4-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865a4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865a4-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="865a4-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="865a4-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="865a4-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865a4-127">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865a4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865a4-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="865a4-128">See also</span></span>

- [<span data-ttu-id="865a4-129">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="865a4-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
