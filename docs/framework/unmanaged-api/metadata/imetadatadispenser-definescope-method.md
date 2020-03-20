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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177643"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="60b57-102">IMetaDataDispenser::DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="60b57-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="60b57-103">Vytvoří novou oblast v paměti, ve které můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="60b57-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60b57-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60b57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60b57-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="60b57-106">[v] CLSID verze metadat struktur, které mají být vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="60b57-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="60b57-107">Tato hodnota musí být CLSID_CorMetaDataRuntime pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="60b57-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="60b57-108">[v] Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="60b57-108">[in] Flags that specify options.</span></span> <span data-ttu-id="60b57-109">Tato hodnota musí být nula pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="60b57-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="60b57-110">[v] IID požadované rozhraní metadat, které mají být vráceny; volající použije rozhraní k vytvoření nových metadat.</span><span class="sxs-lookup"><span data-stu-id="60b57-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="60b57-111">Hodnota `riid` musí určit jedno z rozhraní "emit".</span><span class="sxs-lookup"><span data-stu-id="60b57-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="60b57-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="60b57-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="60b57-113">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="60b57-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60b57-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60b57-114">Remarks</span></span>  
 <span data-ttu-id="60b57-115">`DefineScope`vytvoří sadu tabulek metadat v paměti, vygeneruje jedinečný identifikátor GUID (identifikátor verze modulu nebo MVID) pro metadata a vytvoří položku v tabulce modulu pro vyzařovanou jednotku kompilace.</span><span class="sxs-lookup"><span data-stu-id="60b57-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="60b57-116">Atributy můžete připojit k oboru metadat jako celku pomocí metody [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [IMetaDataEmit::DefineCustomAttribute.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)</span><span class="sxs-lookup"><span data-stu-id="60b57-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60b57-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60b57-117">Requirements</span></span>  
 <span data-ttu-id="60b57-118">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60b57-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60b57-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="60b57-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60b57-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="60b57-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60b57-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60b57-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b57-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="60b57-122">See also</span></span>

- [<span data-ttu-id="60b57-123">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b57-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="60b57-124">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b57-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="60b57-125">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b57-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="60b57-126">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b57-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="60b57-127">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="60b57-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
