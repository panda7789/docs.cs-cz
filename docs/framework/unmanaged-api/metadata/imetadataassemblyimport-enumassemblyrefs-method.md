---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18dda94ac9a19a7cabbaa2a9c4cc83badb079f92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="d6848-102">IMetaDataAssemblyImport::EnumAssemblyRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="d6848-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="d6848-103">Vytvoří výčet `mdAssemblyRef` instancí, které jsou definovány v manifestu sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6848-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6848-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6848-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6848-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6848-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d6848-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="d6848-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d6848-107">Tato hodnota musí být null hodnotu v případě `EnumAssemblyRefs` metoda je volána poprvé.</span><span class="sxs-lookup"><span data-stu-id="d6848-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="d6848-108">[out] Výčet `mdAssemblyRef` tokenů metadat.</span><span class="sxs-lookup"><span data-stu-id="d6848-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6848-109">[v] Maximální počet tokeny, které může být umístěno `rAssemblyRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="d6848-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d6848-110">[out] Počet tokeny, které ve skutečnosti umístěných v `rAssemblyRefs`.</span><span class="sxs-lookup"><span data-stu-id="d6848-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6848-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6848-111">Return Value</span></span>  
  
|<span data-ttu-id="d6848-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6848-112">HRESULT</span></span>|<span data-ttu-id="d6848-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d6848-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6848-114">`EnumAssemblyRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d6848-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6848-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="d6848-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d6848-116">V takovém případě `pcTokens` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="d6848-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6848-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6848-117">Requirements</span></span>  
 <span data-ttu-id="d6848-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6848-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6848-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6848-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6848-120">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6848-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6848-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6848-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6848-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6848-122">See Also</span></span>  
 [<span data-ttu-id="d6848-123">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6848-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
