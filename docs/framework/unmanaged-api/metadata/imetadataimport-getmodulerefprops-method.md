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
ms.openlocfilehash: be4408758db1cbf7839c12cb66ff395625925f69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779024"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="54900-102">IMetaDataImport::GetModuleRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="54900-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="54900-103">Získá název odkazuje token metadat zadaného modulu.</span><span class="sxs-lookup"><span data-stu-id="54900-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54900-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54900-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54900-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54900-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="54900-106">[in] Odkaz ModuleRef tokenu metadat, která odkazuje na modul mají být získány informace metadat.</span><span class="sxs-lookup"><span data-stu-id="54900-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="54900-107">[out] Vyrovnávací paměti, která bude uchovávat název modulu.</span><span class="sxs-lookup"><span data-stu-id="54900-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="54900-108">[in] Požadovaná velikost `szName` v širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="54900-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="54900-109">[out] Vrácená velikost `szName` v širokých znaků.</span><span class="sxs-lookup"><span data-stu-id="54900-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54900-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54900-110">Requirements</span></span>  
 <span data-ttu-id="54900-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54900-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54900-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="54900-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54900-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54900-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54900-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54900-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54900-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54900-115">See also</span></span>

- [<span data-ttu-id="54900-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54900-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="54900-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54900-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
