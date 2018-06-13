---
title: IMetaDataImport::GetModuleRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e8d6549395c6c61f5f94a4b34ad0e3739737ed1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447042"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="8ec18-102">IMetaDataImport::GetModuleRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8ec18-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="8ec18-103">Získá název modulu odkazuje token Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="8ec18-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ec18-104">Syntax</span></span>  
  
```  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ec18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ec18-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="8ec18-106">[v] Odkaz ModuleRef metadata token, který odkazuje na modulu získat informace metadat pro.</span><span class="sxs-lookup"><span data-stu-id="8ec18-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="8ec18-107">[out] Vyrovnávací paměť pro název modulu.</span><span class="sxs-lookup"><span data-stu-id="8ec18-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8ec18-108">[v] Požadovaná velikost `szName` v široké znaky.</span><span class="sxs-lookup"><span data-stu-id="8ec18-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8ec18-109">[out] Vrácený velikost `szName` v široké znaky.</span><span class="sxs-lookup"><span data-stu-id="8ec18-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ec18-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ec18-110">Requirements</span></span>  
 <span data-ttu-id="8ec18-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ec18-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ec18-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8ec18-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ec18-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ec18-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ec18-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec18-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ec18-115">See Also</span></span>  
 [<span data-ttu-id="8ec18-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ec18-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="8ec18-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8ec18-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
