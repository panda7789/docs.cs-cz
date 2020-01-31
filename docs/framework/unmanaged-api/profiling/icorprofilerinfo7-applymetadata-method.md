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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861694"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="33a11-102">ICorProfilerInfo7::ApplyMetaData Method</span><span class="sxs-lookup"><span data-stu-id="33a11-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="33a11-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="33a11-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="33a11-104">Aplikuje metadata nově definovaná metodami `IMetadataEmit::Define*` do zadaného modulu.</span><span class="sxs-lookup"><span data-stu-id="33a11-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a11-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33a11-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33a11-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33a11-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="33a11-107">pro Identifikátor modulu, jehož metadata se změnila.</span><span class="sxs-lookup"><span data-stu-id="33a11-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33a11-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33a11-108">Remarks</span></span>  
 <span data-ttu-id="33a11-109">Pokud jsou změny metadat provedeny po zpětném volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) , je nutné před použitím nových metadat zavolat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="33a11-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="33a11-110">`ApplyMetaData` podporuje pouze přidávání následujících typů metadat:</span><span class="sxs-lookup"><span data-stu-id="33a11-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="33a11-111">`AssemblyRef` záznamy, které vytvoříte voláním metody [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="33a11-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="33a11-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="33a11-112">method.</span></span>  
  
- <span data-ttu-id="33a11-113">`TypeRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="33a11-114">`TypeSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit:: gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="33a11-115">`MemberRef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="33a11-116">`MemberSpec` záznamy, které vytvoříte voláním metody [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="33a11-117">`UserString` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="33a11-118">Počínaje rozhraním .NET Core 3,0 `ApplyMetaData` také podporuje následující typy:</span><span class="sxs-lookup"><span data-stu-id="33a11-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="33a11-119">`TypeDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="33a11-120">`MethodDef` záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="33a11-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="33a11-121">Přidání virtuálních metod do existujícího typu však není podporováno.</span><span class="sxs-lookup"><span data-stu-id="33a11-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="33a11-122">Před zpětným voláním [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) musí být virtuální metody přidané.</span><span class="sxs-lookup"><span data-stu-id="33a11-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="33a11-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33a11-123">Requirements</span></span>  
 <span data-ttu-id="33a11-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33a11-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33a11-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="33a11-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33a11-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33a11-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33a11-127">**Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33a11-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33a11-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33a11-128">See also</span></span>

- [<span data-ttu-id="33a11-129">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="33a11-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
