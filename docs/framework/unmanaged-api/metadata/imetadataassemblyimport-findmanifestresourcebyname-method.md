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
ms.openlocfilehash: ae9097725aecd21e910e49a78d81951df39e9b2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177768"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="fc5bc-102">IMetaDataAssemblyImport::FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="fc5bc-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="fc5bc-103">Získá ukazatel na prostředek manifestu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="fc5bc-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc5bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc5bc-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="fc5bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc5bc-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="fc5bc-106">[v] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="fc5bc-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="fc5bc-107">[out] Pole používané k `mdManifestResource` ukládání tokenů metadat, z nichž každý představuje prostředek manifestu.</span><span class="sxs-lookup"><span data-stu-id="fc5bc-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc5bc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc5bc-108">Remarks</span></span>  
 <span data-ttu-id="fc5bc-109">Metoda `FindManifestResourceByName` používá standardní pravidla používaná za běhu společného jazyka pro řešení odkazů.</span><span class="sxs-lookup"><span data-stu-id="fc5bc-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc5bc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc5bc-110">Requirements</span></span>  
 <span data-ttu-id="fc5bc-111">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc5bc-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc5bc-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="fc5bc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc5bc-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc5bc-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc5bc-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc5bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5bc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc5bc-115">See also</span></span>

- [<span data-ttu-id="fc5bc-116">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc5bc-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="fc5bc-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="fc5bc-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
