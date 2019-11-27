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
ms.openlocfilehash: c3c57074ae53e2e1d8d41aa04cb6eb6089db58b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449439"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="585f5-102">IMetaDataAssemblyImport::GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="585f5-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="585f5-103">Získá sadu vlastností pro sestavení se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="585f5-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="585f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="585f5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="585f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="585f5-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="585f5-106">[in].</span><span class="sxs-lookup"><span data-stu-id="585f5-106">[in].</span></span> <span data-ttu-id="585f5-107">Token metadat `mdAssembly`, který představuje sestavení, pro které mají být získány vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="585f5-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="585f5-108">mimo Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="585f5-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="585f5-109">mimo Počet bajtů ve vráceném veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="585f5-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="585f5-110">mimo Ukazatel na algoritmus použitý k hashování souborů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="585f5-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="585f5-111">mimo Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="585f5-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="585f5-112">pro Velikost v rámci velkých znaků `szName`.</span><span class="sxs-lookup"><span data-stu-id="585f5-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="585f5-113">mimo Počet znaků, které jsou ve skutečnosti vraceny `szName`.</span><span class="sxs-lookup"><span data-stu-id="585f5-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="585f5-114">mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="585f5-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="585f5-115">mimo Příznaky, které popisují metadata použitá pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="585f5-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="585f5-116">Tato hodnota je kombinací jedné nebo více hodnot [CorAssemblyFlags –](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="585f5-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="585f5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="585f5-117">Requirements</span></span>  
 <span data-ttu-id="585f5-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="585f5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="585f5-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="585f5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="585f5-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="585f5-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="585f5-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="585f5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585f5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="585f5-122">See also</span></span>

- [<span data-ttu-id="585f5-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="585f5-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
