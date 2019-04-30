---
title: IMetaDataAssemblyImport::GetAssemblyProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4817a62d276bfdb50bfcbf658f40f5568673bea0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905018"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="6faca-102">IMetaDataAssemblyImport::GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="6faca-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="6faca-103">Získá sadu vlastností pro sestavení s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="6faca-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6faca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6faca-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6faca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6faca-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="6faca-106">[in].</span><span class="sxs-lookup"><span data-stu-id="6faca-106">[in].</span></span> <span data-ttu-id="6faca-107">`mdAssembly` Token metadat, který představuje sestavení, pro které chcete-li získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6faca-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="6faca-108">[out] Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="6faca-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="6faca-109">[out] Počet bajtů vrácených veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="6faca-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="6faca-110">[out] Ukazatel na algoritmus použitý k vytvoření hodnoty hash souborů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="6faca-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="6faca-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="6faca-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6faca-112">[in] Velikost v široké znaky z `szName`.</span><span class="sxs-lookup"><span data-stu-id="6faca-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6faca-113">[out] Počet skutečně vrácených v široké znaky `szName`.</span><span class="sxs-lookup"><span data-stu-id="6faca-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="6faca-114">[out] Ukazatel na assemblymetadata – struktura, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="6faca-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="6faca-115">[out] Příznaky, které popisují metadata použité u sestavení.</span><span class="sxs-lookup"><span data-stu-id="6faca-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="6faca-116">Tato hodnota je kombinace jedné nebo více [corassemblyflags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6faca-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6faca-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6faca-117">Requirements</span></span>  
 <span data-ttu-id="6faca-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6faca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6faca-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6faca-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6faca-120">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6faca-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6faca-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6faca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6faca-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6faca-122">See also</span></span>

- [<span data-ttu-id="6faca-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6faca-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
