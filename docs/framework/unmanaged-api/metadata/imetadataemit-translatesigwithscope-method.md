---
title: "IMetaDataEmit::TranslateSigWithScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.TranslateSigWithScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5127defc97423283b52b7b5bd8c6b7a31104fbc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="61fb5-102">IMetaDataEmit::TranslateSigWithScope – metoda</span><span class="sxs-lookup"><span data-stu-id="61fb5-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="61fb5-103">Importuje sestavení do aktuální obor a získá nové podpis metadata pro sloučené obor.</span><span class="sxs-lookup"><span data-stu-id="61fb5-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61fb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61fb5-104">Syntax</span></span>  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61fb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61fb5-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="61fb5-106">[v] Rozhraní pro import sestavení (kde je definován podpis).</span><span class="sxs-lookup"><span data-stu-id="61fb5-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="61fb5-107">[v] Hodnota hash objektu blob pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="61fb5-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="61fb5-108">[v] Počet bajtů v `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="61fb5-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="61fb5-109">[v] Rozhraní pro import metadat obor.</span><span class="sxs-lookup"><span data-stu-id="61fb5-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="61fb5-110">[v] Podpis určených k importu.</span><span class="sxs-lookup"><span data-stu-id="61fb5-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="61fb5-111">[v] Velikost v bajtech z `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="61fb5-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="61fb5-112">[v] Rozhraní pro export sestavení.</span><span class="sxs-lookup"><span data-stu-id="61fb5-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="61fb5-113">[v] Rozhraní pro export metadat obor.</span><span class="sxs-lookup"><span data-stu-id="61fb5-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="61fb5-114">[out] Vyrovnávací paměti pro uložení objektů blob přeložený podpis.</span><span class="sxs-lookup"><span data-stu-id="61fb5-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="61fb5-115">[v] Kapacitu, v bajtech z `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="61fb5-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="61fb5-116">[out] Počet skutečného bajtů přeložený podpis.</span><span class="sxs-lookup"><span data-stu-id="61fb5-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61fb5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61fb5-117">Requirements</span></span>  
 <span data-ttu-id="61fb5-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61fb5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61fb5-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61fb5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61fb5-120">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61fb5-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61fb5-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61fb5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61fb5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="61fb5-122">See Also</span></span>  
 [<span data-ttu-id="61fb5-123">Imetadataassemblyemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61fb5-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="61fb5-124">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61fb5-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="61fb5-125">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61fb5-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="61fb5-126">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61fb5-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="61fb5-127">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61fb5-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
