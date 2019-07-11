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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8dd1daf3528bbc642033e254a809c18c3662ff1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779182"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="69b56-102">IMetaDataAssemblyImport::GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="69b56-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="69b56-103">Získá sadu vlastností exportovaný typ s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="69b56-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69b56-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="69b56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69b56-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="69b56-106">[in] `mdExportedType` Token metadat, který představuje exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="69b56-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="69b56-107">[out] Název typu exportované.</span><span class="sxs-lookup"><span data-stu-id="69b56-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="69b56-108">[in] Velikost v širokých znaků, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="69b56-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="69b56-109">[out] Počet skutečně vrácených v široké znaky `szName`</span><span class="sxs-lookup"><span data-stu-id="69b56-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="69b56-110">[out] `mdFile`, `mdAssemblyRef`, Nebo `mdExportedType` token metadat, který obsahuje nebo povoluje přístup k vlastnosti exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="69b56-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="69b56-111">[out] Ukazatel `mdTypeDef` token, který představuje typ v souboru.</span><span class="sxs-lookup"><span data-stu-id="69b56-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="69b56-112">[out] Ukazatel na příznaky, které popisují metadata u exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="69b56-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="69b56-113">Příznaky hodnota může být jeden nebo více [cortypeattr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="69b56-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b56-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="69b56-114">Requirements</span></span>  
 <span data-ttu-id="69b56-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69b56-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b56-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69b56-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69b56-117">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69b56-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69b56-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b56-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69b56-119">See also</span></span>

- [<span data-ttu-id="69b56-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="69b56-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
