---
title: IMetaDataImport::GetTypeRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 191a6e4fcfe340ed43e85a9aa90f8a2ec0931730
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671652"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="968f4-102">IMetaDataImport::GetTypeRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="968f4-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="968f4-103">Získá metadata přidružená k <xref:System.Type> odkazuje zadaný token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="968f4-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="968f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="968f4-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="968f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="968f4-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="968f4-106">[in] Token TypeRef, který představuje typ, který chcete vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="968f4-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="968f4-107">[out] Ukazatel na rozsah, ve které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="968f4-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="968f4-108">Tato hodnota je odkaz AssemblyRef nebo Odkaz ModuleRef token.</span><span class="sxs-lookup"><span data-stu-id="968f4-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="968f4-109">[out] Vyrovnávací paměti, který obsahuje název typu.</span><span class="sxs-lookup"><span data-stu-id="968f4-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="968f4-110">[in] Požadovaná velikost v širokých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="968f4-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="968f4-111">[out] Velikost vrácené v širokých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="968f4-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="968f4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="968f4-112">Requirements</span></span>  
 <span data-ttu-id="968f4-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="968f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="968f4-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="968f4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="968f4-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="968f4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="968f4-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="968f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="968f4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="968f4-117">See also</span></span>
- [<span data-ttu-id="968f4-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="968f4-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="968f4-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="968f4-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
