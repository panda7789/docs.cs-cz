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
ms.openlocfilehash: f46033b9e643ef6b4a0063c4995b8c024b8c1f7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175353"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="5f65e-102">IMetaDataImport::GetModuleRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5f65e-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="5f65e-103">Získá název modulu odkazuje zadaný token metadat.</span><span class="sxs-lookup"><span data-stu-id="5f65e-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f65e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f65e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f65e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f65e-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="5f65e-106">[v] Token metadat ModuleRef, který odkazuje na modul získat informace o metadatech.</span><span class="sxs-lookup"><span data-stu-id="5f65e-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="5f65e-107">[out] Vyrovnávací paměť pro uložení názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="5f65e-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5f65e-108">[v] Požadovaná velikost `szName` v širokých znacích.</span><span class="sxs-lookup"><span data-stu-id="5f65e-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="5f65e-109">[out] Vrácená velikost `szName` v širokých znacích.</span><span class="sxs-lookup"><span data-stu-id="5f65e-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f65e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f65e-110">Requirements</span></span>  
 <span data-ttu-id="5f65e-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f65e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f65e-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="5f65e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f65e-113">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5f65e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f65e-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f65e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f65e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f65e-115">See also</span></span>

- [<span data-ttu-id="5f65e-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f65e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5f65e-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f65e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
