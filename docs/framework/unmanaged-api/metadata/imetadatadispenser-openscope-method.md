---
title: IMetaDataDispenser::OpenScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b94987631f7dbbe39e585a8ea2c2252b9427613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079601"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="3ec16-102">IMetaDataDispenser::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="3ec16-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="3ec16-103">Otevření existujícího souboru na disku a mapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="3ec16-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec16-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ec16-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ec16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ec16-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="3ec16-106">[in] Název souboru, který má být otevřen.</span><span class="sxs-lookup"><span data-stu-id="3ec16-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="3ec16-107">Soubor musí obsahovat metadata common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3ec16-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3ec16-108">[in] Hodnota [coropenflags –](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro určení režimu (čtení, zápisu a tak dále) pro otevření.</span><span class="sxs-lookup"><span data-stu-id="3ec16-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="3ec16-109">[in] Identifikátor IID rozhraní požadované metadat má být vrácen. volající budou používat rozhraní pro import (čtení) nebo generování metadat (zápis).</span><span class="sxs-lookup"><span data-stu-id="3ec16-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="3ec16-110">Hodnota `riid` musíte zadat jedno z rozhraní "import" nebo "generování".</span><span class="sxs-lookup"><span data-stu-id="3ec16-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="3ec16-111">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="3ec16-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="3ec16-112">[out] Ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3ec16-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ec16-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ec16-113">Remarks</span></span>  
 <span data-ttu-id="3ec16-114">Kopie v paměti metadat může být dotázán pomocí metody z jednoho z rozhraní "import" nebo přidat do pomocí metod od rozhraní "generování".</span><span class="sxs-lookup"><span data-stu-id="3ec16-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="3ec16-115">Pokud cílový soubor neobsahuje metadat CLR `OpenScope` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3ec16-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="3ec16-116">V rozhraní .NET Framework verze 1.0 a 1.1, pokud obor se otevře s `dwOpenFlags` nastavíte ofRead, je vhodné pro sdílení.</span><span class="sxs-lookup"><span data-stu-id="3ec16-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="3ec16-117">To znamená pokud následných volání `OpenScope` předat mu název souboru, který byl dříve otevřen, existující obor již byl použit a není vytvořena nová sada datových struktur.</span><span class="sxs-lookup"><span data-stu-id="3ec16-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="3ec16-118">Však mohou vzniknout problémy, kvůli toto sdílení.</span><span class="sxs-lookup"><span data-stu-id="3ec16-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="3ec16-119">V rozhraní .NET Framework verze 2.0, otevřeného oborů s `dwOpenFlags` nastavenou na ofRead jsou již sdíleny.</span><span class="sxs-lookup"><span data-stu-id="3ec16-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="3ec16-120">Hodnota ofReadOnly slouží k povolení oboru, který má být sdílené.</span><span class="sxs-lookup"><span data-stu-id="3ec16-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="3ec16-121">Při sdílení obor dotazů, které používají "pro čtení a zápisu" rozhraní metadat se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="3ec16-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec16-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ec16-122">Requirements</span></span>  
 <span data-ttu-id="3ec16-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ec16-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ec16-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ec16-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ec16-125">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ec16-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3ec16-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3ec16-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ec16-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ec16-127">See also</span></span>

- [<span data-ttu-id="3ec16-128">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="3ec16-129">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="3ec16-130">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="3ec16-131">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3ec16-132">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3ec16-133">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="3ec16-134">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3ec16-135">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ec16-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
