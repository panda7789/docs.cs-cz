---
title: IMetaDataImport::GetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a482c7a06efe888408206f2de569e0a8739b85b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777497"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="bf549-102">IMetaDataImport::GetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="bf549-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="bf549-103">Vrátí informace metadat pro <xref:System.Type> reprezentována zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="bf549-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf549-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf549-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bf549-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf549-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bf549-106">[in] Token TypeDef, která představuje typ, který chcete vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="bf549-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="bf549-107">[out] Vyrovnávací paměti, který obsahuje název typu.</span><span class="sxs-lookup"><span data-stu-id="bf549-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="bf549-108">[in] Velikost v širokých znaků `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bf549-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="bf549-109">[out] Počet širokých znaků, které jsou vráceny v `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bf549-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="bf549-110">[out] Ukazatel na libovolný příznaky, které mění definici typu.</span><span class="sxs-lookup"><span data-stu-id="bf549-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="bf549-111">Tato hodnota je bitová maska z [cortypeattr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf549-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="bf549-112">[out] Definice TypeDef nebo TypeRef token metadat, který představuje základní typ požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="bf549-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf549-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bf549-113">Requirements</span></span>  
 <span data-ttu-id="bf549-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf549-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf549-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf549-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf549-116">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf549-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf549-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf549-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf549-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf549-118">See also</span></span>

- [<span data-ttu-id="bf549-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf549-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bf549-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf549-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
