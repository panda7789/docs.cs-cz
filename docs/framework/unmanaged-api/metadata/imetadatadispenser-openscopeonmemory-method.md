---
title: IMetaDataDispenser::OpenScopeOnMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6233e5ecb479db43f35c9d95c42c66c02c81122f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648927"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="e5336-102">IMetaDataDispenser::OpenScopeOnMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="e5336-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="e5336-103">Otevře se oblast paměti, která obsahuje existující metadata.</span><span class="sxs-lookup"><span data-stu-id="e5336-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="e5336-104">To znamená, že tato metoda otevře oblastí paměti, ve kterém existujících dat je považován za metadat.</span><span class="sxs-lookup"><span data-stu-id="e5336-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5336-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5336-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5336-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5336-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="e5336-107">[in] Ukazatel, který určuje počáteční adresu oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="e5336-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="e5336-108">[in] Velikost oblasti paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="e5336-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e5336-109">[in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro určení režimu (čtení, zápisu a tak dále) pro otevření.</span><span class="sxs-lookup"><span data-stu-id="e5336-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="e5336-110">[in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající budou používat rozhraní pro import (čtení) nebo generování metadat (zápis).</span><span class="sxs-lookup"><span data-stu-id="e5336-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="e5336-111">Hodnota `riid` musíte zadat jedno z rozhraní "import" nebo "generování".</span><span class="sxs-lookup"><span data-stu-id="e5336-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="e5336-112">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="e5336-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e5336-113">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e5336-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5336-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5336-114">Remarks</span></span>  
 <span data-ttu-id="e5336-115">Kopie v paměti metadat může být dotázán pomocí metody z jednoho z rozhraní "import" nebo přidat do pomocí metod od rozhraní "generování".</span><span class="sxs-lookup"><span data-stu-id="e5336-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="e5336-116">`OpenScopeOnMemory` Metoda je podobná [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) metody, s tím rozdílem, že metadata zájmu již existuje v paměti, nikoli v souboru na disku.</span><span class="sxs-lookup"><span data-stu-id="e5336-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="e5336-117">Pokud cílové oblasti paměti neobsahuje metadata common language runtime (CLR), `OpenScopeOnMemory` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e5336-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5336-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5336-118">Requirements</span></span>  
 <span data-ttu-id="e5336-119">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5336-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5336-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5336-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5336-121">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5336-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5336-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5336-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5336-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5336-123">See also</span></span>
- [<span data-ttu-id="e5336-124">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="e5336-125">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="e5336-126">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="e5336-127">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="e5336-128">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e5336-129">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e5336-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e5336-131">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5336-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
