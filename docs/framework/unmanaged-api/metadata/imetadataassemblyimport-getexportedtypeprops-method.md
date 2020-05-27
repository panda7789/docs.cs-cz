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
ms.openlocfilehash: 944941c2356cae93ecc85f1714b4b29aefcb50ad
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008401"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="8b489-102">IMetaDataAssemblyImport::GetExportedTypeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="8b489-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="8b489-103">Získá sadu vlastností exportovaného typu se zadaným podpisem metadat.</span><span class="sxs-lookup"><span data-stu-id="8b489-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b489-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b489-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8b489-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b489-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="8b489-106">pro `mdExportedType`Token metadat, který představuje exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="8b489-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="8b489-107">mimo Název exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8b489-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8b489-108">pro Velikost (v rámci velkých znaků) `szName` .</span><span class="sxs-lookup"><span data-stu-id="8b489-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8b489-109">mimo Počet skutečně vrácených znaků`szName`</span><span class="sxs-lookup"><span data-stu-id="8b489-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="8b489-110">mimo `mdFile` `mdAssemblyRef` Token metadat, nebo `mdExportedType` , který obsahuje nebo umožňuje přístup k vlastnostem exportovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8b489-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="8b489-111">mimo Ukazatel na `mdTypeDef` token, který představuje typ v souboru.</span><span class="sxs-lookup"><span data-stu-id="8b489-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="8b489-112">mimo Ukazatel na příznaky, které popisují metadata použitá pro exportovaný typ.</span><span class="sxs-lookup"><span data-stu-id="8b489-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="8b489-113">Hodnota příznaků může být jedna nebo víc hodnot [CorTypeAttr –](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="8b489-113">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b489-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b489-114">Requirements</span></span>  
 <span data-ttu-id="8b489-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b489-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b489-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b489-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b489-117">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="8b489-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b489-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b489-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b489-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b489-119">See also</span></span>

- [<span data-ttu-id="8b489-120">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b489-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
