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
ms.openlocfilehash: cea84f47a5289df4bc9c50381e18d7077b3b8dad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440470"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="52d60-102">IMetaDataEmit::TranslateSigWithScope – metoda</span><span class="sxs-lookup"><span data-stu-id="52d60-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="52d60-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span><span class="sxs-lookup"><span data-stu-id="52d60-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52d60-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="52d60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52d60-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="52d60-106">[in] The interface for import assembly (where the signature is defined).</span><span class="sxs-lookup"><span data-stu-id="52d60-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="52d60-107">[in] The hash blob for the assembly.</span><span class="sxs-lookup"><span data-stu-id="52d60-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="52d60-108">[in] The count of bytes in `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="52d60-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="52d60-109">[in] The interface for import metadata scope.</span><span class="sxs-lookup"><span data-stu-id="52d60-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="52d60-110">[in] The signature to be imported.</span><span class="sxs-lookup"><span data-stu-id="52d60-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="52d60-111">[in] The size, in bytes, of `pbSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="52d60-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="52d60-112">[in] The interface for export assembly.</span><span class="sxs-lookup"><span data-stu-id="52d60-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="52d60-113">[in] The interface for export metadata scope.</span><span class="sxs-lookup"><span data-stu-id="52d60-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="52d60-114">[out] The buffer to hold the translated signature blob.</span><span class="sxs-lookup"><span data-stu-id="52d60-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="52d60-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span><span class="sxs-lookup"><span data-stu-id="52d60-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="52d60-116">[out] The number of actual bytes in the translated signature.</span><span class="sxs-lookup"><span data-stu-id="52d60-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52d60-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52d60-117">Requirements</span></span>  
 <span data-ttu-id="52d60-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52d60-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52d60-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52d60-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52d60-120">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="52d60-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52d60-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52d60-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d60-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52d60-122">See also</span></span>

- [<span data-ttu-id="52d60-123">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52d60-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="52d60-124">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52d60-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="52d60-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52d60-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="52d60-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52d60-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="52d60-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52d60-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
