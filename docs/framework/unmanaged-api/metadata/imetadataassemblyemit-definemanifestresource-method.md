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
ms.openlocfilehash: 48d688b64bbe9330a176ef073e96865b719ff2c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446678"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="ea820-102">IMetaDataAssemblyEmit::DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="ea820-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="ea820-103">Vytvoří `ManifestResource` struktury obsahující metadata pro zadanou prostředku manifestu a vrátí token přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="ea820-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea820-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea820-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea820-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea820-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ea820-106">[v] Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="ea820-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="ea820-107">[v] Token metadata typu `mdtFile` nebo `mdtAssemblyRef` která se mapuje na zprostředkovateli prostředků.</span><span class="sxs-lookup"><span data-stu-id="ea820-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="ea820-108">Hodnota NULL označuje, že je soubor, ve kterém se vloží metadata poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="ea820-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ea820-109">[v] Posun na začátek prostředků v rámci tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="ea820-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="ea820-110">Pro prostředky v samostatné soubory bude vždy nula.</span><span class="sxs-lookup"><span data-stu-id="ea820-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="ea820-111">Pokud prostředek je vložen soubor PE (přenosné spustitelný soubor), je to posun objektů BLOB, který se spustí v umístění zadaném v záhlaví souboru cor.h prostředku.</span><span class="sxs-lookup"><span data-stu-id="ea820-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="ea820-112">[v] Bitová kombinace hodnot příznaku, které určují nastavení vlastností pro definici prostředků.</span><span class="sxs-lookup"><span data-stu-id="ea820-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="ea820-113">[out] Ukazatel na token vrácený metadat.</span><span class="sxs-lookup"><span data-stu-id="ea820-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea820-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea820-114">Remarks</span></span>  
 <span data-ttu-id="ea820-115">Jeden `ManifestResource` pro každý prostředek, který je implementována ve všech souborů sestavení musí být definován strukturu metadat.</span><span class="sxs-lookup"><span data-stu-id="ea820-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea820-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea820-116">Requirements</span></span>  
 <span data-ttu-id="ea820-117">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea820-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea820-118">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ea820-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ea820-119">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ea820-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ea820-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea820-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea820-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea820-121">See Also</span></span>  
 [<span data-ttu-id="ea820-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ea820-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
