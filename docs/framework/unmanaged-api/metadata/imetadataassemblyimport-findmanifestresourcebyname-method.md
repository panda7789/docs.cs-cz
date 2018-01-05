---
title: "IMetaDataAssemblyImport::FindManifestResourceByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.FindManifestResourceByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d6cc738c227157b45e242fb46a672d28d6ce778
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="7317c-102">IMetaDataAssemblyImport::FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="7317c-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="7317c-103">Získá ukazatel na prostředku manifestu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="7317c-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7317c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7317c-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="7317c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7317c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="7317c-106">[v] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="7317c-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="7317c-107">[out] Pole používá k ukládání `mdManifestResource` tokenů metadat, z nichž každý představuje prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="7317c-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7317c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7317c-108">Remarks</span></span>  
 <span data-ttu-id="7317c-109">`FindManifestResourceByName` Metoda používá standardní pravidla zaměstnaní modul common language runtime pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="7317c-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7317c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7317c-110">Requirements</span></span>  
 <span data-ttu-id="7317c-111">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7317c-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7317c-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7317c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7317c-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7317c-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7317c-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7317c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7317c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7317c-115">See Also</span></span>  
 [<span data-ttu-id="7317c-116">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7317c-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="7317c-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="7317c-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
