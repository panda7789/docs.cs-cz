---
title: "IMetaDataImport::EnumProperties – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63ff10904440f55ec3fe6fb6aa581fbf560763e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="b34ec-102">IMetaDataImport::EnumProperties – metoda</span><span class="sxs-lookup"><span data-stu-id="b34ec-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="b34ec-103">Vytvoří výčet představující vlastnosti typu odkazuje zadaný token TypeDef tokeny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b34ec-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b34ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b34ec-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b34ec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b34ec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b34ec-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b34ec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b34ec-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="b34ec-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="b34ec-108">[v] TypeDef token představující typu s vlastnostmi výčet.</span><span class="sxs-lookup"><span data-stu-id="b34ec-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="b34ec-109">[out] Pole používá k ukládání tokeny vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b34ec-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b34ec-110">[v] Maximální velikost `rProperties` pole.</span><span class="sxs-lookup"><span data-stu-id="b34ec-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="b34ec-111">[out] Číslo, vrátí se v tokenů vlastnosti `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="b34ec-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b34ec-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b34ec-112">Return Value</span></span>  
  
|<span data-ttu-id="b34ec-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b34ec-113">HRESULT</span></span>|<span data-ttu-id="b34ec-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b34ec-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b34ec-115">`EnumProperties`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b34ec-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b34ec-116">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="b34ec-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="b34ec-117">V takovém případě `pcProperties` je nulová.</span><span class="sxs-lookup"><span data-stu-id="b34ec-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b34ec-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b34ec-118">Requirements</span></span>  
 <span data-ttu-id="b34ec-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b34ec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b34ec-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b34ec-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b34ec-121">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b34ec-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b34ec-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b34ec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34ec-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="b34ec-123">See Also</span></span>  
 [<span data-ttu-id="b34ec-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b34ec-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b34ec-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b34ec-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
