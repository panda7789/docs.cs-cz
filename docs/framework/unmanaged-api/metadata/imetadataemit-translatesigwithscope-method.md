---
title: IMetaDataEmit::TranslateSigWithScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c571e37d87ffd136687452dc80a823b8ddbe3359
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782060"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="2888f-102">IMetaDataEmit::TranslateSigWithScope – metoda</span><span class="sxs-lookup"><span data-stu-id="2888f-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="2888f-103">Importuje sestavení do aktuální obor a získá nový podpis metadat pro sloučený obor.</span><span class="sxs-lookup"><span data-stu-id="2888f-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2888f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2888f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="2888f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2888f-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="2888f-106">[in] Rozhraní pro import sestavení (kde je definován podpis).</span><span class="sxs-lookup"><span data-stu-id="2888f-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="2888f-107">[in] Objekt blob algoritmu hash pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="2888f-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="2888f-108">[in] Počet bajtů v `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="2888f-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="2888f-109">[in] Rozhraní pro oboru importu metadat.</span><span class="sxs-lookup"><span data-stu-id="2888f-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="2888f-110">[in] Podpis k importu.</span><span class="sxs-lookup"><span data-stu-id="2888f-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="2888f-111">[in] Velikost v bajtech, z `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="2888f-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="2888f-112">[in] Rozhraní pro export sestavení.</span><span class="sxs-lookup"><span data-stu-id="2888f-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="2888f-113">[in] Rozhraní pro export metadat obor.</span><span class="sxs-lookup"><span data-stu-id="2888f-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="2888f-114">[out] Vyrovnávací paměť pro uložení objektů blob přeložené podpis.</span><span class="sxs-lookup"><span data-stu-id="2888f-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="2888f-115">[in] Kapacita, v bajtech, z `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="2888f-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="2888f-116">[out] Počet skutečný počet bajtů v přeložené podpisu.</span><span class="sxs-lookup"><span data-stu-id="2888f-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2888f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2888f-117">Requirements</span></span>  
 <span data-ttu-id="2888f-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2888f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2888f-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2888f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2888f-120">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2888f-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2888f-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2888f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2888f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2888f-122">See also</span></span>

- [<span data-ttu-id="2888f-123">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2888f-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="2888f-124">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2888f-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="2888f-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2888f-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2888f-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2888f-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="2888f-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2888f-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
