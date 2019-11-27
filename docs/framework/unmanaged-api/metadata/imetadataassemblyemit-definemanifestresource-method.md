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
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432062"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="96739-102">IMetaDataAssemblyEmit::DefineManifestResource – metoda</span><span class="sxs-lookup"><span data-stu-id="96739-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="96739-103">Vytvoří strukturu `ManifestResource` obsahující metadata pro zadaný prostředek manifestu a vrátí přidružený token metadat.</span><span class="sxs-lookup"><span data-stu-id="96739-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96739-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96739-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96739-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96739-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="96739-106">pro Název prostředku.</span><span class="sxs-lookup"><span data-stu-id="96739-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="96739-107">pro Token metadat typu `mdtFile` nebo `mdtAssemblyRef`, který se mapuje na poskytovatele prostředků.</span><span class="sxs-lookup"><span data-stu-id="96739-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="96739-108">Hodnota NULL znamená, že soubor, ve kterém jsou vložená metadata, je poskytovatel prostředků.</span><span class="sxs-lookup"><span data-stu-id="96739-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="96739-109">pro Posun na začátek prostředku v rámci souboru.</span><span class="sxs-lookup"><span data-stu-id="96739-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="96739-110">U prostředků v samostatných souborech bude tato hodnota vždy nulová.</span><span class="sxs-lookup"><span data-stu-id="96739-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="96739-111">Pokud je prostředek vložen do přenositelného spustitelného souboru (PE), jedná se o posun objektu BLOB prostředku, který začíná v umístění zadaném v souboru hlaviček cor. h.</span><span class="sxs-lookup"><span data-stu-id="96739-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="96739-112">pro Bitová kombinace hodnot příznaků, které určují nastavení vlastností pro definici prostředků.</span><span class="sxs-lookup"><span data-stu-id="96739-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="96739-113">mimo Ukazatel na vrácený token metadat.</span><span class="sxs-lookup"><span data-stu-id="96739-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96739-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96739-114">Remarks</span></span>  
 <span data-ttu-id="96739-115">Pro každý prostředek, který je implementován v každém souboru sestavení, musí být definována jedna `ManifestResource` struktura metadat.</span><span class="sxs-lookup"><span data-stu-id="96739-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96739-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96739-116">Requirements</span></span>  
 <span data-ttu-id="96739-117">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96739-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96739-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="96739-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96739-119">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="96739-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96739-120">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96739-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96739-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96739-121">See also</span></span>

- [<span data-ttu-id="96739-122">IMetaDataAssemblyEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96739-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
