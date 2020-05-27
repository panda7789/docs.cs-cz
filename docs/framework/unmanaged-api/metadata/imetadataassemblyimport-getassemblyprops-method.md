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
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009051"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="3cf6f-102">IMetaDataAssemblyImport::GetAssemblyProps – metoda</span><span class="sxs-lookup"><span data-stu-id="3cf6f-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="3cf6f-103">Získá sadu vlastností pro sestavení se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf6f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3cf6f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3cf6f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf6f-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="3cf6f-106">[in].</span><span class="sxs-lookup"><span data-stu-id="3cf6f-106">[in].</span></span> <span data-ttu-id="3cf6f-107">`mdAssembly`Token metadat představující sestavení, pro které mají být získány vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="3cf6f-108">mimo Ukazatel na veřejný klíč nebo token metadat.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="3cf6f-109">mimo Počet bajtů ve vráceném veřejném klíči.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="3cf6f-110">mimo Ukazatel na algoritmus použitý k hashování souborů v sestavení.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="3cf6f-111">mimo Jednoduchý název sestavení.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3cf6f-112">pro Velikost ve velkých znakech `szName` .</span><span class="sxs-lookup"><span data-stu-id="3cf6f-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="3cf6f-113">mimo Počet skutečně vrácených znaků `szName` .</span><span class="sxs-lookup"><span data-stu-id="3cf6f-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="3cf6f-114">mimo Ukazatel na strukturu AssemblyMetadata –, která obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="3cf6f-115">mimo Příznaky, které popisují metadata použitá pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="3cf6f-116">Tato hodnota je kombinací jedné nebo více hodnot [CorAssemblyFlags –](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3cf6f-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf6f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cf6f-117">Requirements</span></span>  
 <span data-ttu-id="3cf6f-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cf6f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cf6f-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3cf6f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cf6f-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="3cf6f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cf6f-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf6f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf6f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cf6f-122">See also</span></span>

- [<span data-ttu-id="3cf6f-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cf6f-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
