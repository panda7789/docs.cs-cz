---
title: IMetaDataAssemblyImport::EnumManifestResources – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449556"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="a2635-102">IMetaDataAssemblyImport::EnumManifestResources – metoda</span><span class="sxs-lookup"><span data-stu-id="a2635-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="a2635-103">Získá ukazatel na enumerátor pro prostředky, na které se odkazuje v aktuálním manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="a2635-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2635-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2635-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a2635-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2635-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a2635-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a2635-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="a2635-107">Při prvním volání metody `EnumManifestResources` musí být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="a2635-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="a2635-108">mimo Pole, které se používá k uložení `mdManifestResource` tokenů metadat</span><span class="sxs-lookup"><span data-stu-id="a2635-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a2635-109">pro Maximální počet `mdManifestResource` tokenů, které lze umístit do `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="a2635-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a2635-110">mimo Počet tokenů `mdManifestResource` vlastněných v `rManifestResources`.</span><span class="sxs-lookup"><span data-stu-id="a2635-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2635-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a2635-111">Return Value</span></span>  
  
|<span data-ttu-id="a2635-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a2635-112">HRESULT</span></span>|<span data-ttu-id="a2635-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a2635-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a2635-114">`EnumManifestResources` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a2635-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a2635-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="a2635-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a2635-116">V takovém případě je `pcTokens` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="a2635-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2635-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a2635-117">Requirements</span></span>  
 <span data-ttu-id="a2635-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2635-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2635-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a2635-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2635-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="a2635-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2635-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2635-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2635-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2635-122">See also</span></span>

- [<span data-ttu-id="a2635-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a2635-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
