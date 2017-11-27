---
title: "IMetaDataEmit::DefineTypeRefByName – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineTypeRefByName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9ce04733fa9f149f155d850c53b65b263943cf8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="2776a-102">IMetaDataEmit::DefineTypeRefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="2776a-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="2776a-103">Získá token metadat pro typ, který je definován v zadaném oboru, který není v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="2776a-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2776a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2776a-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2776a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2776a-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="2776a-106">[v] Token zadání oboru rozlišení.</span><span class="sxs-lookup"><span data-stu-id="2776a-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="2776a-107">Platné jsou následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="2776a-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="2776a-108">`mdModuleRef`, pokud typ je definovaná ve stejném sestavení, ve kterém je definovaný volající.</span><span class="sxs-lookup"><span data-stu-id="2776a-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="2776a-109">`mdAssemblyRef`, pokud typ je definována v sestavení než ten, ve kterém je definovaný volající.</span><span class="sxs-lookup"><span data-stu-id="2776a-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="2776a-110">`mdTypeRef`, pokud je typ vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="2776a-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="2776a-111">`mdModule`, pokud typ je definovaná ve stejném modulu, ve kterém je definovaný volající.</span><span class="sxs-lookup"><span data-stu-id="2776a-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="2776a-112">Hodnota Null, pokud typ je definována globálně.</span><span class="sxs-lookup"><span data-stu-id="2776a-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="2776a-113">[v] Název cílového typu ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="2776a-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="2776a-114">[out] Ukazatel `mdTypeRef` token, který je přiřazen k typu.</span><span class="sxs-lookup"><span data-stu-id="2776a-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2776a-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2776a-115">Requirements</span></span>  
 <span data-ttu-id="2776a-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2776a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2776a-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2776a-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2776a-118">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2776a-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2776a-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2776a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2776a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="2776a-120">See Also</span></span>  
 [<span data-ttu-id="2776a-121">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2776a-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2776a-122">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2776a-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
