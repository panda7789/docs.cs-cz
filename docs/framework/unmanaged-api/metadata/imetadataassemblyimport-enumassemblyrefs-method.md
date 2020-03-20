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
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177832"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="41307-102">IMetaDataAssemblyImport::EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="41307-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="41307-103">Vyjmenovává `mdAssemblyRef` instance, které jsou definovány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="41307-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41307-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41307-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41307-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41307-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="41307-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="41307-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="41307-107">To musí být hodnota `EnumAssemblyRefs` null při první volání metody.</span><span class="sxs-lookup"><span data-stu-id="41307-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="41307-108">[out] Výčet tokenů `mdAssemblyRef` metadat.</span><span class="sxs-lookup"><span data-stu-id="41307-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="41307-109">[v] Maximální počet tokenů, které mohou `rAssemblyRefs` být umístěny v poli.</span><span class="sxs-lookup"><span data-stu-id="41307-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="41307-110">[out] Počet tokenů skutečně umístěných v `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="41307-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41307-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="41307-111">Return Value</span></span>  
  
|<span data-ttu-id="41307-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41307-112">HRESULT</span></span>|<span data-ttu-id="41307-113">Popis</span><span class="sxs-lookup"><span data-stu-id="41307-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="41307-114">`EnumAssemblyRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="41307-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="41307-115">Neexistují žádné tokeny výčet.</span><span class="sxs-lookup"><span data-stu-id="41307-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="41307-116">V tomto `pcTokens` případě je nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="41307-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41307-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41307-117">Requirements</span></span>  
 <span data-ttu-id="41307-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41307-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41307-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="41307-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41307-120">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41307-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41307-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41307-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41307-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="41307-122">See also</span></span>

- [<span data-ttu-id="41307-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41307-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
