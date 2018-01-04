---
title: "IMetaDataImport::GetModuleRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetModuleRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee230b691411c49ba4f0096d998ac229283fc02c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="47092-102">IMetaDataImport::GetModuleRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="47092-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="47092-103">Získá název modulu odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="47092-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47092-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47092-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47092-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47092-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="47092-106">[v] Odkaz ModuleRef metadata token, který odkazuje na modulu získat informace metadat pro.</span><span class="sxs-lookup"><span data-stu-id="47092-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="47092-107">[out] Vyrovnávací paměť pro název modulu.</span><span class="sxs-lookup"><span data-stu-id="47092-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="47092-108">[v] Požadovaná velikost `szName` v široké znaky.</span><span class="sxs-lookup"><span data-stu-id="47092-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="47092-109">[out] Vrácený velikost `szName` v široké znaky.</span><span class="sxs-lookup"><span data-stu-id="47092-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47092-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47092-110">Requirements</span></span>  
 <span data-ttu-id="47092-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47092-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47092-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47092-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47092-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47092-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47092-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47092-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47092-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="47092-115">See Also</span></span>  
 [<span data-ttu-id="47092-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47092-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="47092-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47092-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
