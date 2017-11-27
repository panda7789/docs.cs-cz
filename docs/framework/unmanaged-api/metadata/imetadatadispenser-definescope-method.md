---
title: "IMetaDataDispenser::DefineScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.DefineScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 964e6df1b6aba7ca85b627cf19c38f5df600b6ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="78848-102">IMetaDataDispenser::DefineScope – metoda</span><span class="sxs-lookup"><span data-stu-id="78848-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="78848-103">Vytvoří novou oblast v paměti, ve kterém můžete vytvořit nová metadata.</span><span class="sxs-lookup"><span data-stu-id="78848-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78848-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78848-104">Syntax</span></span>  
  
```  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78848-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78848-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="78848-106">[v] CLSID verzi struktury metadat, který se má vytvořit.</span><span class="sxs-lookup"><span data-stu-id="78848-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="78848-107">Tato hodnota musí být CLSID_CorMetaDataRuntime pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="78848-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="78848-108">[v] Příznaky, které určují možnosti.</span><span class="sxs-lookup"><span data-stu-id="78848-108">[in] Flags that specify options.</span></span> <span data-ttu-id="78848-109">Tato hodnota musí být nula pro rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="78848-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="78848-110">[v] Identifikátory IID rozhraní požadované metadata má být vrácen. volající použije k vytvoření nové metadat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78848-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="78848-111">Hodnota `riid` musíte zadat jednu z rozhraní "emitování".</span><span class="sxs-lookup"><span data-stu-id="78848-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="78848-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit nebo IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="78848-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="78848-113">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="78848-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78848-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78848-114">Remarks</span></span>  
 <span data-ttu-id="78848-115">`DefineScope`Vytvoří sadu tabulek v paměti metadata, generuje jedinečný identifikátor GUID (identifikátor verze modulu nebo identifikátoru MVID) pro metadata a vytvoří záznam v tabulce modulu pro jednotku kompilace se vygenerované.</span><span class="sxs-lookup"><span data-stu-id="78848-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="78848-116">Atributy můžete připojit k oboru metadat jako celek s použitím [imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) nebo [imetadataemit::definecustomattribute –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) metoda, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="78848-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78848-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78848-117">Requirements</span></span>  
 <span data-ttu-id="78848-118">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78848-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78848-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78848-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78848-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78848-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78848-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78848-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78848-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="78848-122">See Also</span></span>  
 [<span data-ttu-id="78848-123">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78848-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="78848-124">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78848-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="78848-125">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78848-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="78848-126">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78848-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="78848-127">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78848-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
