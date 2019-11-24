---
title: IMetaDataDispenser::DefineScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 381c38542dcde242c0a1a4e71e9b99316328159d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436244"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="75d20-102">IMetaDataDispenser::DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="75d20-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="75d20-103">Creates a new area in memory in which you can create new metadata.</span><span class="sxs-lookup"><span data-stu-id="75d20-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75d20-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75d20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="75d20-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="75d20-106">[in] The CLSID of the version of metadata structures to be created.</span><span class="sxs-lookup"><span data-stu-id="75d20-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="75d20-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="75d20-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="75d20-108">[in] Flags that specify options.</span><span class="sxs-lookup"><span data-stu-id="75d20-108">[in] Flags that specify options.</span></span> <span data-ttu-id="75d20-109">This value must be zero for the .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="75d20-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="75d20-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span><span class="sxs-lookup"><span data-stu-id="75d20-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="75d20-111">The value of `riid` must specify one of the "emit" interfaces.</span><span class="sxs-lookup"><span data-stu-id="75d20-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="75d20-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="75d20-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="75d20-113">[out] The pointer to the returned interface.</span><span class="sxs-lookup"><span data-stu-id="75d20-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75d20-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75d20-114">Remarks</span></span>  
 <span data-ttu-id="75d20-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span><span class="sxs-lookup"><span data-stu-id="75d20-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="75d20-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span><span class="sxs-lookup"><span data-stu-id="75d20-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75d20-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75d20-117">Requirements</span></span>  
 <span data-ttu-id="75d20-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75d20-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75d20-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="75d20-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75d20-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="75d20-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="75d20-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75d20-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75d20-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75d20-122">See also</span></span>

- [<span data-ttu-id="75d20-123">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d20-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="75d20-124">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d20-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="75d20-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d20-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="75d20-126">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d20-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="75d20-127">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75d20-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
