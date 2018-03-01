---
title: "IMetaDataImport::GetMethodProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e4e0ae7dfed4b13ea83e16d6380443c9d1b72b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="034c6-102">IMetaDataImport::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="034c6-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="034c6-103">Získá metadata přidružená metoda odkazuje zadaný MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="034c6-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="034c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="034c6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="034c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="034c6-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="034c6-106">[v] MethodDef token, který představuje metodu vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="034c6-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="034c6-107">[out] Ukazatel na TypeDef token, který představuje typ, který implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="034c6-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="034c6-108">[out] Ukazatel na vyrovnávací paměť, která má název metody.</span><span class="sxs-lookup"><span data-stu-id="034c6-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="034c6-109">[v] Požadovaná velikost `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="034c6-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="034c6-110">[out] Ukazatel na velikost v široké znaky `szMethod`, nebo v případě zkrácení, skutečný počet široké znaky v názvu metody.</span><span class="sxs-lookup"><span data-stu-id="034c6-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="034c6-111">[out] Ukazatel na žádné příznaky přidružené k metodě.</span><span class="sxs-lookup"><span data-stu-id="034c6-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="034c6-112">[out] Ukazatel na binární metadata podpis metody.</span><span class="sxs-lookup"><span data-stu-id="034c6-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="034c6-113">[out] Ukazatel na velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="034c6-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="034c6-114">[out] Ukazatel na adresu relativní virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="034c6-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="034c6-115">[out] Ukazatel na žádné příznaky implementace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="034c6-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="034c6-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="034c6-116">Requirements</span></span>  
 <span data-ttu-id="034c6-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="034c6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="034c6-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="034c6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="034c6-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="034c6-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="034c6-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="034c6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="034c6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="034c6-121">See Also</span></span>  
 [<span data-ttu-id="034c6-122">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="034c6-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="034c6-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="034c6-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
