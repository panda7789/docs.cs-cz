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
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003952"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="3c780-102">IMetaDataEmit::TranslateSigWithScope – metoda</span><span class="sxs-lookup"><span data-stu-id="3c780-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="3c780-103">Importuje sestavení do aktuálního oboru a získá nový podpis metadat pro sloučený obor.</span><span class="sxs-lookup"><span data-stu-id="3c780-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c780-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c780-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3c780-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c780-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="3c780-106">pro Rozhraní pro import sestavení (kde je definován podpis).</span><span class="sxs-lookup"><span data-stu-id="3c780-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="3c780-107">pro Objekt BLOB algoritmu hash pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c780-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="3c780-108">pro Počet bajtů v `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="3c780-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="3c780-109">pro Rozhraní pro obor metadat pro import.</span><span class="sxs-lookup"><span data-stu-id="3c780-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="3c780-110">pro Podpis, který se má importovat</span><span class="sxs-lookup"><span data-stu-id="3c780-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3c780-111">pro Velikost v bajtech `pbSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="3c780-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="3c780-112">pro Rozhraní pro export sestavení.</span><span class="sxs-lookup"><span data-stu-id="3c780-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="3c780-113">pro Rozhraní pro obor metadat pro export.</span><span class="sxs-lookup"><span data-stu-id="3c780-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="3c780-114">mimo Vyrovnávací paměť pro uchování přeloženého objektu BLOB signatury.</span><span class="sxs-lookup"><span data-stu-id="3c780-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="3c780-115">pro Kapacita (v bajtech) `pvTranslatedSig` .</span><span class="sxs-lookup"><span data-stu-id="3c780-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="3c780-116">mimo Počet skutečných bajtů v přeloženém podpisu.</span><span class="sxs-lookup"><span data-stu-id="3c780-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c780-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c780-117">Requirements</span></span>  
 <span data-ttu-id="3c780-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c780-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c780-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3c780-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3c780-120">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="3c780-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c780-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c780-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c780-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c780-122">See also</span></span>

- [<span data-ttu-id="3c780-123">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c780-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="3c780-124">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c780-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3c780-125">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c780-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3c780-126">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c780-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="3c780-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c780-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
