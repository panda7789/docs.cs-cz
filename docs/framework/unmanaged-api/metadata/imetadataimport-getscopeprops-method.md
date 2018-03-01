---
title: "IMetaDataImport::GetScopeProps – metoda"
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
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53e77a7bf0bd0aafc205469c4e101f8bfdcbe80b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="0f75e-102">IMetaDataImport::GetScopeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0f75e-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="0f75e-103">Získá název a volitelně identifikátor verze sestavení nebo modul v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0f75e-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f75e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f75e-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f75e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f75e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0f75e-106">[out] Vyrovnávací paměť pro název sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="0f75e-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0f75e-107">[v] Velikost v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="0f75e-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0f75e-108">[out] Počet široké znaky, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="0f75e-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="0f75e-109">[na víc systémů, volitelné] Ukazatel na identifikátor GUID, který jednoznačně identifikuje verzi sestavení nebo modul.</span><span class="sxs-lookup"><span data-stu-id="0f75e-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f75e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f75e-110">Remarks</span></span>  
 <span data-ttu-id="0f75e-111">[Imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda se používá k nastavení těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="0f75e-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f75e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f75e-112">Requirements</span></span>  
 <span data-ttu-id="0f75e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f75e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f75e-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0f75e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f75e-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f75e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f75e-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f75e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f75e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f75e-117">See Also</span></span>  
 [<span data-ttu-id="0f75e-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f75e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0f75e-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f75e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
