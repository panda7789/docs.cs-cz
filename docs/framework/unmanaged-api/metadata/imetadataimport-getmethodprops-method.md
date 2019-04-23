---
title: IMetaDataImport::GetMethodProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c61931f5f6a4bbbf66446d68b0d1b2d1df958a66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137915"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="4e047-102">IMetaDataImport::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="4e047-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="4e047-103">Získá token budou metadata spojená s metodou odkazuje zadaný MethodDef.</span><span class="sxs-lookup"><span data-stu-id="4e047-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e047-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e047-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e047-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e047-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="4e047-106">[in] Token MethodDef, který představuje metodu vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="4e047-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="4e047-107">[out] Ukazatel, který představuje typ, který implementuje metodu token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="4e047-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="4e047-108">[out] Ukazatel do vyrovnávací paměti, který má název metody.</span><span class="sxs-lookup"><span data-stu-id="4e047-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="4e047-109">[in] Požadovaná velikost `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="4e047-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="4e047-110">[out] Ukazatel na velikost v širokých znaků `szMethod`, nebo v případě zkrácení, skutečný počet širokých znaků v názvu metody.</span><span class="sxs-lookup"><span data-stu-id="4e047-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="4e047-111">[out] Ukazatel na libovolný příznaky spojené s metodou.</span><span class="sxs-lookup"><span data-stu-id="4e047-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="4e047-112">[out] Ukazatel na binární metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="4e047-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="4e047-113">[out] Ukazatel na velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="4e047-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="4e047-114">[out] Ukazatel na relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="4e047-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="4e047-115">[out] Ukazatel na libovolný příznaky implementace metody.</span><span class="sxs-lookup"><span data-stu-id="4e047-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e047-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e047-116">Requirements</span></span>  
 <span data-ttu-id="4e047-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e047-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e047-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4e047-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e047-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4e047-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4e047-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e047-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e047-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e047-121">See also</span></span>

- [<span data-ttu-id="4e047-122">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e047-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4e047-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e047-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
