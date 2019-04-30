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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b617e29e2df22b59114c8b978daa645de1cc6176
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905252"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="a603f-102">IMetaDataAssemblyEmit::DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="a603f-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="a603f-103">Vytvoří `ManifestResource` struktury obsahující metadata pro zadaný prostředek manifestu a vrátí token metadat.</span><span class="sxs-lookup"><span data-stu-id="a603f-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a603f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a603f-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a603f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a603f-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a603f-106">[in] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="a603f-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="a603f-107">[in] Token metadat typu `mdtFile` nebo `mdtAssemblyRef` , který se mapuje na poskytovateli prostředků.</span><span class="sxs-lookup"><span data-stu-id="a603f-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="a603f-108">Hodnota NULL označuje, že je soubor, ve kterém se vloží metadata poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="a603f-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="a603f-109">[in] Posun k začátku prostředků v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="a603f-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="a603f-110">Pro prostředky v samostatné soubory bude vždy nula.</span><span class="sxs-lookup"><span data-stu-id="a603f-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="a603f-111">Pokud je prostředek vložený v souboru PE (portable executable), je to posun objektu BLOB, který spouští v umístění zadaném v souboru hlaviček cor.h prostředku.</span><span class="sxs-lookup"><span data-stu-id="a603f-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="a603f-112">[in] Bitová kombinace hodnot příznaků, které určují nastavení vlastností pro definici prostředků.</span><span class="sxs-lookup"><span data-stu-id="a603f-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="a603f-113">[out] Ukazatel na token vrácený metadat.</span><span class="sxs-lookup"><span data-stu-id="a603f-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a603f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a603f-114">Remarks</span></span>  
 <span data-ttu-id="a603f-115">Jeden `ManifestResource` struktury metadat musí být definované pro každý prostředek, který je implementován v každém ze souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="a603f-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a603f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a603f-116">Requirements</span></span>  
 <span data-ttu-id="a603f-117">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a603f-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a603f-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a603f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a603f-119">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a603f-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a603f-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a603f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a603f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a603f-121">See also</span></span>

- [<span data-ttu-id="a603f-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a603f-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
