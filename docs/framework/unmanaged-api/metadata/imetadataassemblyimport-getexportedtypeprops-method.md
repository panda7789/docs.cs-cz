---
title: IMetaDataAssemblyImport::GetExportedTypeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177762"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="e3c01-102">IMetaDataAssemblyImport::GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="e3c01-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="e3c01-103">Získá sadu vlastností exportovaného typu se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="e3c01-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3c01-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c01-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="e3c01-106">[v] Token `mdExportedType` metadat, který představuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="e3c01-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="e3c01-107">[out] Název exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="e3c01-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e3c01-108">[v] Velikost . `szName`</span><span class="sxs-lookup"><span data-stu-id="e3c01-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="e3c01-109">[out] Počet širokých znaků skutečně vrácených`szName`</span><span class="sxs-lookup"><span data-stu-id="e3c01-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="e3c01-110">[out] Token `mdFile` `mdAssemblyRef`, `mdExportedType` nebo metadata, který obsahuje nebo umožňuje přístup k vlastnostem exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="e3c01-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="e3c01-111">[out] Ukazatel na `mdTypeDef` token, který představuje typ v souboru.</span><span class="sxs-lookup"><span data-stu-id="e3c01-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="e3c01-112">[out] Ukazatel na příznaky, které popisují metadata použitá pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="e3c01-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="e3c01-113">Hodnota příznaky může být jeden nebo více [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e3c01-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c01-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3c01-114">Requirements</span></span>  
 <span data-ttu-id="e3c01-115">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c01-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c01-116">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="e3c01-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e3c01-117">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3c01-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e3c01-118">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c01-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c01-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3c01-119">See also</span></span>

- [<span data-ttu-id="e3c01-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3c01-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
