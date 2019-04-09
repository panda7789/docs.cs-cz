---
title: IMetaDataEmit::DefineTypeRefByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93c55cec3d35fd4208a4a8a7c9b235dd10fb9ca
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156166"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="58811-102">IMetaDataEmit::DefineTypeRefByName – metoda</span><span class="sxs-lookup"><span data-stu-id="58811-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="58811-103">Získá token metadat pro typ, který je definován v zadaném rozsahu, který se nenachází v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="58811-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58811-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58811-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58811-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="58811-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="58811-106">[in] Token určující rozlišovací obor.</span><span class="sxs-lookup"><span data-stu-id="58811-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="58811-107">Platné jsou následující typy tokenů:</span><span class="sxs-lookup"><span data-stu-id="58811-107">The following token types are valid:</span></span>  
  
-   `mdModuleRef`<span data-ttu-id="58811-108">, pokud je typ definován ve stejném sestavení, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="58811-108">, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   `mdAssemblyRef`<span data-ttu-id="58811-109">, pokud je typ definovaný v jiném sestavení než ten, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="58811-109">, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   `mdTypeRef`<span data-ttu-id="58811-110">, pokud je typ vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="58811-110">, if the type is a nested type.</span></span>  
  
-   `mdModule`<span data-ttu-id="58811-111">, pokud je typ definován ve stejném modulu, ve kterém je definována volající.</span><span class="sxs-lookup"><span data-stu-id="58811-111">, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="58811-112">Hodnota Null, pokud je typ definován globálně.</span><span class="sxs-lookup"><span data-stu-id="58811-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="58811-113">[in] Název cílového typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="58811-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="58811-114">[out] Ukazatel `mdTypeRef` token, který je přiřazen k typu.</span><span class="sxs-lookup"><span data-stu-id="58811-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58811-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58811-115">Requirements</span></span>  
 <span data-ttu-id="58811-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58811-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58811-117">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="58811-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="58811-118">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="58811-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="58811-119">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="58811-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58811-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58811-120">See also</span></span>

- [<span data-ttu-id="58811-121">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58811-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="58811-122">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="58811-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
