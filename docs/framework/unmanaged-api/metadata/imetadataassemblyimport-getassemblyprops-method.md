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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177785"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="b1779-102">IMetaDataAssemblyImport::GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="b1779-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="b1779-103">Získá sadu vlastností pro sestavení se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="b1779-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1779-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1779-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="b1779-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1779-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="b1779-106">[v].</span><span class="sxs-lookup"><span data-stu-id="b1779-106">[in].</span></span> <span data-ttu-id="b1779-107">Token `mdAssembly` metadat, který představuje sestavení, pro které chcete získat vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b1779-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="b1779-108">[out] Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="b1779-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b1779-109">[out] Počet bajtů ve vráceném veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="b1779-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="b1779-110">[out] Ukazatel na algoritmus použitý k algoritmu hash soubory v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1779-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1779-111">[out] Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1779-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b1779-112">[v] Velikost , v širokých `szName`znaků, .</span><span class="sxs-lookup"><span data-stu-id="b1779-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b1779-113">[out] Počet širokých znaků skutečně `szName`vrátil v .</span><span class="sxs-lookup"><span data-stu-id="b1779-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b1779-114">[out] Ukazatel na strukturu ASSEMBLYMETADATA, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1779-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="b1779-115">[out] Příznaky, které popisují metadata použitá v sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1779-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="b1779-116">Tato hodnota je kombinací jedné nebo více hodnot [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b1779-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1779-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1779-117">Requirements</span></span>  
 <span data-ttu-id="b1779-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1779-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1779-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="b1779-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1779-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1779-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1779-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1779-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1779-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1779-122">See also</span></span>

- [<span data-ttu-id="b1779-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1779-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
