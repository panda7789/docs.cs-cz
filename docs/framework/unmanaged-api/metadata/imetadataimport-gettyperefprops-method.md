---
title: "IMetaDataImport::GetTypeRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetTypeRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 23dbfe2468088da5e02fb7156606af5f3fa51044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="1f125-102">IMetaDataImport::GetTypeRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="1f125-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="1f125-103">Získá metadata přidružená <xref:System.Type> odkazuje zadaný odkaz TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="1f125-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f125-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f125-104">Syntax</span></span>  
  
```  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f125-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f125-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="1f125-106">[v] Odkaz TypeRef token, který představuje typ vrátit metadata pro.</span><span class="sxs-lookup"><span data-stu-id="1f125-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="1f125-107">[out] Ukazatel na obor, ve které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="1f125-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="1f125-108">Tato hodnota je odkaz AssemblyRef nebo Odkaz ModuleRef token.</span><span class="sxs-lookup"><span data-stu-id="1f125-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="1f125-109">[out] Vyrovnávací paměť, která obsahuje název typu.</span><span class="sxs-lookup"><span data-stu-id="1f125-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1f125-110">[v] Požadovaná velikost v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="1f125-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1f125-111">[out] Vrácený velikost v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="1f125-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f125-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f125-112">Requirements</span></span>  
 <span data-ttu-id="1f125-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f125-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f125-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1f125-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f125-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f125-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f125-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f125-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f125-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f125-117">See Also</span></span>  
 [<span data-ttu-id="1f125-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f125-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="1f125-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1f125-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
