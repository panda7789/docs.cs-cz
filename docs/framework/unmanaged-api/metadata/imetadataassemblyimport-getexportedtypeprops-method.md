---
title: "IMetaDataAssemblyImport::GetExportedTypeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="311c4-102">IMetaDataAssemblyImport::GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="311c4-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="311c4-103">Získá sadu vlastností typu exportovaný podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="311c4-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="311c4-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="311c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="311c4-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="311c4-106">[v] `mdExportedType` Metadata token, který představuje typ exportovaný.</span><span class="sxs-lookup"><span data-stu-id="311c4-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="311c4-107">[out] Název typu exportovaný.</span><span class="sxs-lookup"><span data-stu-id="311c4-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="311c4-108">[v] Velikost v široké znaky z `szName`.</span><span class="sxs-lookup"><span data-stu-id="311c4-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="311c4-109">[out] Počet aktuálně vrácenou široké znaky`szName`</span><span class="sxs-lookup"><span data-stu-id="311c4-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="311c4-110">[out] `mdFile`, `mdAssemblyRef`, Nebo `mdExportedType` metadata token, který obsahuje nebo povoluje přístup k vlastnosti exportovaný typu.</span><span class="sxs-lookup"><span data-stu-id="311c4-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="311c4-111">[out] Ukazatel na `mdTypeDef` token, který představuje typ v souboru.</span><span class="sxs-lookup"><span data-stu-id="311c4-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="311c4-112">[out] Ukazatel na příznaky, které popisují metadata použít u exportovaných typu.</span><span class="sxs-lookup"><span data-stu-id="311c4-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="311c4-113">Příznaky hodnota může být jeden nebo více [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnoty.</span><span class="sxs-lookup"><span data-stu-id="311c4-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="311c4-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="311c4-114">Requirements</span></span>  
 <span data-ttu-id="311c4-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="311c4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311c4-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="311c4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="311c4-117">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="311c4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="311c4-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="311c4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311c4-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="311c4-119">See Also</span></span>  
 [<span data-ttu-id="311c4-120">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="311c4-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
