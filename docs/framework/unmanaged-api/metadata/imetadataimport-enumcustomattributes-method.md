---
title: "IMetaDataImport::EnumCustomAttributes – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumCustomAttributes
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e45c15f3d09972d1c83c9b330965c4e8afd21b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="659ad-102">IMetaDataImport::EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="659ad-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="659ad-103">Vytvoří výčet vlastní definice atributu tokeny spojených s zadaný typ nebo člen.</span><span class="sxs-lookup"><span data-stu-id="659ad-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="659ad-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="659ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="659ad-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="659ad-106">[ve out] Ukazatel na vrácený enumerátor.</span><span class="sxs-lookup"><span data-stu-id="659ad-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="659ad-107">[v] Token pro obor výčtu nebo nula pro všechny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="659ad-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="659ad-108">[v] Token pro konstruktor typu atributy, které mají být ve výčtu, nebo `null` pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="659ad-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="659ad-109">[out] Pole vlastních atributů tokeny.</span><span class="sxs-lookup"><span data-stu-id="659ad-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="659ad-110">[v] Maximální velikost `rCustomAttributes` pole.</span><span class="sxs-lookup"><span data-stu-id="659ad-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="659ad-111">[na víc systémů, volitelné] Skutečný počet tokenu hodnot vrácených v `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="659ad-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="659ad-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="659ad-112">Return Value</span></span>  
  
|<span data-ttu-id="659ad-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="659ad-113">HRESULT</span></span>|<span data-ttu-id="659ad-114">Popis</span><span class="sxs-lookup"><span data-stu-id="659ad-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="659ad-115">`EnumCustomAttributes`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="659ad-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="659ad-116">Neexistují žádné vlastní atributy pro vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="659ad-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="659ad-117">V takovém případě `pcCustomAttributes` je nulová.</span><span class="sxs-lookup"><span data-stu-id="659ad-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="659ad-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="659ad-118">Requirements</span></span>  
 <span data-ttu-id="659ad-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="659ad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="659ad-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="659ad-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="659ad-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="659ad-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="659ad-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="659ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659ad-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="659ad-123">See Also</span></span>  
 [<span data-ttu-id="659ad-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="659ad-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="659ad-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="659ad-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
