---
title: "IMetaDataDispenser::OpenScopeOnMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScopeOnMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0c6cfc21a5aecfc043a7720959610210df1d15ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="7076b-102">IMetaDataDispenser::OpenScopeOnMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="7076b-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="7076b-103">Otevře se oblast paměti, který obsahuje existující metadata.</span><span class="sxs-lookup"><span data-stu-id="7076b-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="7076b-104">To znamená tato metoda otevře určené oblasti paměti, ve kterém se stávající data považuje za metadat.</span><span class="sxs-lookup"><span data-stu-id="7076b-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7076b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7076b-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7076b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7076b-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="7076b-107">[v] Ukazatele, který určuje počáteční adresa oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="7076b-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7076b-108">[v] Velikost oblasti paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="7076b-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7076b-109">[v] Hodnota [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro otevírání zadejte režim (čtení, zápisu a tak dále).</span><span class="sxs-lookup"><span data-stu-id="7076b-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="7076b-110">[v] Identifikátory IID rozhraní požadované metadata má být vrácen. volající se použít rozhraní pro import (čtení) nebo emitování metadata (zápisu).</span><span class="sxs-lookup"><span data-stu-id="7076b-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="7076b-111">Hodnota `riid` musíte zadat jednu z "import" nebo "emitování" rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7076b-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="7076b-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="7076b-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7076b-113">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="7076b-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7076b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7076b-114">Remarks</span></span>  
 <span data-ttu-id="7076b-115">Kopie v paměti metadat můžete položit dotaz na metodami z jednoho z rozhraní "import", nebo přidat do pomocí metod od verze rozhraní "emitování".</span><span class="sxs-lookup"><span data-stu-id="7076b-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="7076b-116">`OpenScopeOnMemory` Metoda je podobná [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metoda, s tím rozdílem, že metadata týkající se již existuje v paměti, a nikoli v souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="7076b-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="7076b-117">Pokud cílovou oblast paměti neobsahuje common language runtime (CLR) metadata, `OpenScopeOnMemory` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7076b-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7076b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7076b-118">Requirements</span></span>  
 <span data-ttu-id="7076b-119">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7076b-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7076b-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7076b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7076b-121">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7076b-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7076b-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7076b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7076b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7076b-123">See Also</span></span>  
 [<span data-ttu-id="7076b-124">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="7076b-125">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="7076b-126">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="7076b-127">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="7076b-128">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7076b-129">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="7076b-130">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="7076b-131">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7076b-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
