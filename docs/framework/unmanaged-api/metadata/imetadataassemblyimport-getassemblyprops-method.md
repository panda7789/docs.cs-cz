---
title: "IMetaDataAssemblyImport::GetAssemblyProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e99474fea329f53286d698d0e1a302909d5cc65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="37456-102">IMetaDataAssemblyImport::GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="37456-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="37456-103">Získá sadu vlastností pro sestavení s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="37456-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37456-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37456-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37456-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37456-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="37456-106">[v].</span><span class="sxs-lookup"><span data-stu-id="37456-106">[in].</span></span> <span data-ttu-id="37456-107">`mdAssembly` Metadata token, který představuje sestavení, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="37456-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="37456-108">[out] Ukazatel na veřejný klíč, nebo token pro metadata.</span><span class="sxs-lookup"><span data-stu-id="37456-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="37456-109">[out] Počet bajtů vrácených veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="37456-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="37456-110">[out] Ukazatel na algoritmus použitý k hodnoty hash souborů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="37456-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="37456-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="37456-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="37456-112">[v] Velikost v široké znaků, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="37456-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="37456-113">[out] Počet široké znaků ve skutečnosti, vrátí se v `szName`.</span><span class="sxs-lookup"><span data-stu-id="37456-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="37456-114">[out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="37456-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="37456-115">[out] Příznaky, které popisují metadata použijí k sestavení.</span><span class="sxs-lookup"><span data-stu-id="37456-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="37456-116">Tato hodnota je kombinací jednoho nebo více [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="37456-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37456-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37456-117">Requirements</span></span>  
 <span data-ttu-id="37456-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37456-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37456-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="37456-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="37456-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="37456-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37456-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37456-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37456-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="37456-122">See Also</span></span>  
 [<span data-ttu-id="37456-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37456-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
