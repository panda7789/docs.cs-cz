---
title: IMetaDataImport::EnumProperties – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b42c558009c25adfd7d282da905e7182dfd3342
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467014"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="952fe-102">IMetaDataImport::EnumProperties – metoda</span><span class="sxs-lookup"><span data-stu-id="952fe-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="952fe-103">Vytvoří výčet vlastnosti tokeny představující vlastnosti typu odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="952fe-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="952fe-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="952fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="952fe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="952fe-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="952fe-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="952fe-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="952fe-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="952fe-108">[in] Token TypeDef představující typ výčet s vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="952fe-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="952fe-109">[out] Pole pro ukládání tokenů vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="952fe-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="952fe-110">[in] Maximální velikost `rProperties` pole.</span><span class="sxs-lookup"><span data-stu-id="952fe-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="952fe-111">[out] Počet tokenů vlastnosti vrácené v `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="952fe-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="952fe-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="952fe-112">Return Value</span></span>  
  
|<span data-ttu-id="952fe-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="952fe-113">HRESULT</span></span>|<span data-ttu-id="952fe-114">Popis</span><span class="sxs-lookup"><span data-stu-id="952fe-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="952fe-115">`EnumProperties` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="952fe-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="952fe-116">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="952fe-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="952fe-117">V takovém případě `pcProperties` je nula.</span><span class="sxs-lookup"><span data-stu-id="952fe-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="952fe-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="952fe-118">Requirements</span></span>  
 <span data-ttu-id="952fe-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952fe-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952fe-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="952fe-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="952fe-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="952fe-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="952fe-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952fe-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952fe-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="952fe-123">See also</span></span>
- [<span data-ttu-id="952fe-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="952fe-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="952fe-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="952fe-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
