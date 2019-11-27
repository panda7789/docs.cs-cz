---
title: IMetaDataAssemblyImport::EnumAssemblyRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450344"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="187ae-102">IMetaDataAssemblyImport::EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="187ae-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="187ae-103">Vytvoří výčet instancí `mdAssemblyRef`, které jsou definovány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="187ae-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="187ae-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="187ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="187ae-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="187ae-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="187ae-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="187ae-107">Při prvním volání metody `EnumAssemblyRefs` musí být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="187ae-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="187ae-108">mimo Výčet `mdAssemblyRef` tokeny metadat</span><span class="sxs-lookup"><span data-stu-id="187ae-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="187ae-109">pro Maximální počet tokenů, které lze umístit do pole `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="187ae-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="187ae-110">mimo Počet tokenů skutečně umístěných v `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="187ae-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="187ae-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="187ae-111">Return Value</span></span>  
  
|<span data-ttu-id="187ae-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="187ae-112">HRESULT</span></span>|<span data-ttu-id="187ae-113">Popis</span><span class="sxs-lookup"><span data-stu-id="187ae-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="187ae-114">`EnumAssemblyRefs` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="187ae-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="187ae-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="187ae-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="187ae-116">V takovém případě je `pcTokens` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="187ae-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="187ae-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="187ae-117">Requirements</span></span>  
 <span data-ttu-id="187ae-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="187ae-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187ae-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="187ae-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="187ae-120">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="187ae-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="187ae-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="187ae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187ae-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="187ae-122">See also</span></span>

- [<span data-ttu-id="187ae-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="187ae-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
