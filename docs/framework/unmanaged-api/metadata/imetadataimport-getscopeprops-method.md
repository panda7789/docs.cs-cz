---
title: IMetaDataImport::GetScopeProps – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e5d998bd85f1cc872acde74fdf954299a279c40
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466268"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="9165e-102">IMetaDataImport::GetScopeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="9165e-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="9165e-103">Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="9165e-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9165e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9165e-104">Syntax</span></span>  
  
```  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9165e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9165e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="9165e-106">[out] Vyrovnávací paměť pro název sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="9165e-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9165e-107">[in] Velikost v širokých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="9165e-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9165e-108">[out] Počet širokých znaků, které jsou vráceny v `szName`.</span><span class="sxs-lookup"><span data-stu-id="9165e-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="9165e-109">[out, volitelné] Ukazatel na identifikátor GUID, který jednoznačně identifikuje verzi sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="9165e-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9165e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9165e-110">Remarks</span></span>  
 <span data-ttu-id="9165e-111">[Imetadataemit::setmoduleprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) metoda se používá k nastavení těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="9165e-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9165e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9165e-112">Requirements</span></span>  
 <span data-ttu-id="9165e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9165e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9165e-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9165e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9165e-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9165e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9165e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9165e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9165e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9165e-117">See also</span></span>
- [<span data-ttu-id="9165e-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9165e-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9165e-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9165e-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
