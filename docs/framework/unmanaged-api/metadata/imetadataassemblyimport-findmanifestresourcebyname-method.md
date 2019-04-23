---
title: IMetaDataAssemblyImport::FindManifestResourceByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf61da362251577acadb83915404eba7508b3099
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141567"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="6cebd-102">IMetaDataAssemblyImport::FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="6cebd-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="6cebd-103">Získá ukazatel na prostředek manifestu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="6cebd-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cebd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cebd-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="6cebd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6cebd-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6cebd-106">[in] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="6cebd-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="6cebd-107">[out] Pole používá k ukládání `mdManifestResource` tokeny metadat, z nichž každý představuje prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="6cebd-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cebd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cebd-108">Remarks</span></span>  
 <span data-ttu-id="6cebd-109">`FindManifestResourceByName` Metoda používá standardní pravidla náhradník modul common language runtime k vyřešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="6cebd-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cebd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cebd-110">Requirements</span></span>  
 <span data-ttu-id="6cebd-111">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cebd-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cebd-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6cebd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cebd-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cebd-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cebd-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cebd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cebd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cebd-115">See also</span></span>

- [<span data-ttu-id="6cebd-116">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cebd-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6cebd-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="6cebd-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
