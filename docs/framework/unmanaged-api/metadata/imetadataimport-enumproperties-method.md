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
ms.openlocfilehash: 64e6bd57c5f16b0e7d59f6cf760030aab4c6b9f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568800"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="ab086-102">IMetaDataImport::EnumProperties – metoda</span><span class="sxs-lookup"><span data-stu-id="ab086-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="ab086-103">Vytvoří výčet vlastnosti tokeny představující vlastnosti typu odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="ab086-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab086-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab086-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab086-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab086-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ab086-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ab086-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ab086-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="ab086-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="ab086-108">[in] Token TypeDef představující typ výčet s vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="ab086-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="ab086-109">[out] Pole pro ukládání tokenů vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ab086-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ab086-110">[in] Maximální velikost `rProperties` pole.</span><span class="sxs-lookup"><span data-stu-id="ab086-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="ab086-111">[out] Počet tokenů vlastnosti vrácené v `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="ab086-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab086-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ab086-112">Return Value</span></span>  
  
|<span data-ttu-id="ab086-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab086-113">HRESULT</span></span>|<span data-ttu-id="ab086-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ab086-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ab086-115">`EnumProperties` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ab086-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ab086-116">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="ab086-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="ab086-117">V takovém případě `pcProperties` je nula.</span><span class="sxs-lookup"><span data-stu-id="ab086-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab086-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab086-118">Requirements</span></span>  
 <span data-ttu-id="ab086-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab086-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab086-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ab086-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab086-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab086-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab086-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab086-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab086-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ab086-123">See also</span></span>
- [<span data-ttu-id="ab086-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab086-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ab086-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ab086-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
