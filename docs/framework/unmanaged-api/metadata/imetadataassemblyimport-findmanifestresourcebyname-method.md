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
ms.openlocfilehash: f0c390509a698fdc4682ba81182d4b407d8718c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448250"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="98d3d-102">IMetaDataAssemblyImport::FindManifestResourceByName – metoda</span><span class="sxs-lookup"><span data-stu-id="98d3d-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>
<span data-ttu-id="98d3d-103">Získá ukazatel na prostředek manifestu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="98d3d-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98d3d-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,   
    [out] mdManifestResource     *ptkManifestResource  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="98d3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98d3d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="98d3d-106">pro Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="98d3d-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="98d3d-107">mimo Pole, které se používá k uložení `mdManifestResource` tokenů metadat, z nichž každý představuje prostředek manifestu.</span><span class="sxs-lookup"><span data-stu-id="98d3d-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98d3d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98d3d-108">Remarks</span></span>  
 <span data-ttu-id="98d3d-109">Metoda `FindManifestResourceByName` používá standardní pravidla zaměstnaná modulem CLR (Common Language Runtime) pro překládání odkazů.</span><span class="sxs-lookup"><span data-stu-id="98d3d-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d3d-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98d3d-110">Requirements</span></span>  
 <span data-ttu-id="98d3d-111">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d3d-111">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d3d-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="98d3d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98d3d-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="98d3d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98d3d-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d3d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d3d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98d3d-115">See also</span></span>

- [<span data-ttu-id="98d3d-116">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="98d3d-116">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="98d3d-117">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="98d3d-117">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
