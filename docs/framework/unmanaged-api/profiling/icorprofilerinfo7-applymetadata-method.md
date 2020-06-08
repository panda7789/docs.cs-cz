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
ms.openlocfilehash: c30206145d08a22af49c4a6a0dc83fd7382bcc06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495503"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="de6a7-102">ICorProfilerInfo7:: ApplyMetaData – metoda</span><span class="sxs-lookup"><span data-stu-id="de6a7-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="de6a7-103">[Podporováno v .NET Framework 4.6.1 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="de6a7-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="de6a7-104">Aplikuje metadata nově definovaná `IMetadataEmit::Define*` metodami na zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="de6a7-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de6a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de6a7-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de6a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de6a7-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="de6a7-107">pro Identifikátor modulu, jehož metadata se změnila.</span><span class="sxs-lookup"><span data-stu-id="de6a7-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de6a7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de6a7-108">Remarks</span></span>  
 <span data-ttu-id="de6a7-109">Pokud jsou změny metadat provedeny po zpětném volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) , je nutné před použitím nových metadat zavolat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="de6a7-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="de6a7-110">`ApplyMetaData`podporuje přidávání následujících typů metadat:</span><span class="sxs-lookup"><span data-stu-id="de6a7-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="de6a7-111">`AssemblyRef`záznamy, které vytvoříte voláním [IMetaDataAssemblyEmit::D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="de6a7-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="de6a7-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="de6a7-112">method.</span></span>  
  
- <span data-ttu-id="de6a7-113">`TypeRef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="de6a7-114">`TypeSpec`záznamy, které vytvoříte voláním metody [IMetaDataEmit:: gettokenfromtypespec –](../metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="de6a7-115">`MemberRef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="de6a7-116">`MemberSpec`záznamy, které vytvoříte voláním metody [IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="de6a7-117">`UserString`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="de6a7-118">Počínaje platformou .NET Core 3,0 `ApplyMetaData` podporuje také následující typy:</span><span class="sxs-lookup"><span data-stu-id="de6a7-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="de6a7-119">`TypeDef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="de6a7-120">`MethodDef`záznamy, které vytvoříte voláním metody [IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="de6a7-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="de6a7-121">Přidání virtuálních metod do existujícího typu však není podporováno.</span><span class="sxs-lookup"><span data-stu-id="de6a7-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="de6a7-122">Před zpětným voláním [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) musí být virtuální metody přidané.</span><span class="sxs-lookup"><span data-stu-id="de6a7-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="de6a7-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de6a7-123">Requirements</span></span>  
 <span data-ttu-id="de6a7-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de6a7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de6a7-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="de6a7-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de6a7-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de6a7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de6a7-127">**Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de6a7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6a7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de6a7-128">See also</span></span>

- [<span data-ttu-id="de6a7-129">ICorProfilerInfo7 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de6a7-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
