---
title: "IMetaDataDispenser::OpenScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenser.OpenScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09c057f42bb849b89d78d2d32af6637640ad22ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="ea7a8-102">IMetaDataDispenser::OpenScope – metoda</span><span class="sxs-lookup"><span data-stu-id="ea7a8-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="ea7a8-103">Otevře existujícího souboru na disku a mapuje jeho metadata do paměti.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea7a8-104">Syntax</span></span>  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea7a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea7a8-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="ea7a8-106">[v] Název souboru, který se otevřít.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="ea7a8-107">Soubor musí obsahovat běžná metadata language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="ea7a8-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="ea7a8-108">[v] Hodnota [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) výčtu pro otevírání zadejte režim (čtení, zápisu a tak dále).</span><span class="sxs-lookup"><span data-stu-id="ea7a8-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="ea7a8-109">[v] Identifikátory IID rozhraní požadované metadata má být vrácen. volající se použít rozhraní pro import (čtení) nebo emitování metadata (zápisu).</span><span class="sxs-lookup"><span data-stu-id="ea7a8-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="ea7a8-110">Hodnota `riid` musíte zadat jednu z "import" nebo "emitování" rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="ea7a8-111">Platné hodnoty jsou IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 nebo IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="ea7a8-112">[out] Ukazatel rozhraní vrácená.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea7a8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea7a8-113">Remarks</span></span>  
 <span data-ttu-id="ea7a8-114">Kopie v paměti metadat můžete položit dotaz na metodami z jednoho z rozhraní "import", nebo přidat do pomocí metod od verze rozhraní "emitování".</span><span class="sxs-lookup"><span data-stu-id="ea7a8-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="ea7a8-115">Pokud cílový soubor neobsahuje CLR metadata `OpenScope` metoda se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="ea7a8-116">V rozhraní .NET Framework verze 1.0 a 1.1, pokud obor je otevřen s `dwOpenFlags` nastavení ofRead, je vhodné pro sdílení.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="ea7a8-117">To znamená pokud následných volání `OpenScope` průchodu názvu souboru, který byl dříve otevřen, se znovu použije stávající oboru a novou sadu datové struktury nebyl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="ea7a8-118">Problémy se však, může dojít z důvodu této sdílení.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="ea7a8-119">V rozhraní .NET Framework verze 2.0, otevřené obory se `dwOpenFlags` nastaven na ofRead jsou již sdíleny.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="ea7a8-120">Použijte hodnotu ofReadOnly umožňující oboru ke sdílení.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="ea7a8-121">Pokud je sdílen obor, dotazy, které používají "pro čtení a zápis" rozhraní metadat se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="ea7a8-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea7a8-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea7a8-122">Requirements</span></span>  
 <span data-ttu-id="ea7a8-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea7a8-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea7a8-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea7a8-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea7a8-125">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea7a8-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea7a8-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea7a8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7a8-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea7a8-127">See Also</span></span>  
 [<span data-ttu-id="ea7a8-128">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [<span data-ttu-id="ea7a8-129">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="ea7a8-130">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="ea7a8-131">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="ea7a8-132">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ea7a8-133">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="ea7a8-134">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ea7a8-135">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea7a8-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
