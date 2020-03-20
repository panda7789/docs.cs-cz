---
title: IMetaDataAssemblyEmit::DefineManifestResource – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177861"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="b0576-102">IMetaDataAssemblyEmit::DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="b0576-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="b0576-103">Vytvoří `ManifestResource` strukturu obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="b0576-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0576-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0576-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b0576-106">[v] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="b0576-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="b0576-107">[v] Token metadat typu `mdtFile` nebo `mdtAssemblyRef` který se mapuje na poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="b0576-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="b0576-108">Hodnota NULL označuje, že soubor, ve kterém jsou metadata vložena, je poskytovatelem prostředků.</span><span class="sxs-lookup"><span data-stu-id="b0576-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="b0576-109">[v] Posun na začátek prostředku v souboru.</span><span class="sxs-lookup"><span data-stu-id="b0576-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="b0576-110">Pro prostředky v samostatných souborech to bude vždy nula.</span><span class="sxs-lookup"><span data-stu-id="b0576-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="b0576-111">Pokud je prostředek vložen do souboru PE (přenosný spustitelný soubor), jedná se o posun objektu BLOB prostředku, který začíná v umístění určeném v souboru hlavičky cor.h.</span><span class="sxs-lookup"><span data-stu-id="b0576-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="b0576-112">[v] Bitová kombinace hodnot příznaku, které určují nastavení vlastností pro definici prostředku.</span><span class="sxs-lookup"><span data-stu-id="b0576-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="b0576-113">[out] Ukazatel na vrácený token metadat.</span><span class="sxs-lookup"><span data-stu-id="b0576-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0576-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0576-114">Remarks</span></span>  
 <span data-ttu-id="b0576-115">Pro `ManifestResource` každý prostředek, který je implementován v každém souboru sestavení, musí být definována jedna struktura metadat.</span><span class="sxs-lookup"><span data-stu-id="b0576-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0576-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0576-116">Requirements</span></span>  
 <span data-ttu-id="b0576-117">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0576-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0576-118">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="b0576-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0576-119">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0576-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0576-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0576-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0576-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0576-121">See also</span></span>

- [<span data-ttu-id="b0576-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0576-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
