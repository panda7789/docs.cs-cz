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
ms.openlocfilehash: 492f8a50c421df56d1b2f79d15d86ef3251b401e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="f428a-102">IMetaDataAssemblyImport::FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="f428a-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="f428a-103">Získá ukazatel na prostředku manifestu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="f428a-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f428a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f428a-104">Syntax</span></span>  
  
```  
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="f428a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f428a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f428a-106">[v] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="f428a-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="f428a-107">[out] Pole používá k ukládání `mdManifestResource` tokenů metadat, z nichž každý představuje prostředku manifestu.</span><span class="sxs-lookup"><span data-stu-id="f428a-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f428a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f428a-108">Remarks</span></span>  
 <span data-ttu-id="f428a-109">`FindManifestResourceByName` Metoda používá standardní pravidla zaměstnaní modul common language runtime pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="f428a-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f428a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f428a-110">Requirements</span></span>  
 <span data-ttu-id="f428a-111">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f428a-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f428a-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f428a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f428a-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f428a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f428a-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f428a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f428a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f428a-115">See Also</span></span>  
 [<span data-ttu-id="f428a-116">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f428a-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="f428a-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="f428a-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
