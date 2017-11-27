---
title: "IMetaDataImport::GetTypeDefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1025ffde2bd066c81c4c562c0dd86e829fc2aef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="a5fcf-102">IMetaDataImport::GetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="a5fcf-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="a5fcf-103">Vrátí informace metadat pro <xref:System.Type> reprezentována zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5fcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5fcf-104">Syntax</span></span>  
  
```  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5fcf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5fcf-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a5fcf-106">[v] TypeDef token, který představuje typ vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="a5fcf-107">[out] Vyrovnávací paměť, která obsahuje název typu.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="a5fcf-108">[v] Velikost v široké znaky `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="a5fcf-109">[out] Počet široké znaky, vrátí se v `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="a5fcf-110">[out] Ukazatel na žádné příznaky, které upravit definici typu.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="a5fcf-111">Tato hodnota je bitová maska z [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="a5fcf-112">[out] TypeDef nebo Odkaz TypeRef metadata token, který představuje základní typ požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="a5fcf-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5fcf-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5fcf-113">Requirements</span></span>  
 <span data-ttu-id="a5fcf-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5fcf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5fcf-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a5fcf-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5fcf-116">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5fcf-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5fcf-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5fcf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fcf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5fcf-118">See Also</span></span>  
 [<span data-ttu-id="a5fcf-119">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5fcf-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a5fcf-120">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5fcf-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
