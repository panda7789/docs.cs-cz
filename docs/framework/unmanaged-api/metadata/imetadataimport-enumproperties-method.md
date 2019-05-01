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
ms.openlocfilehash: 410fd7a702d3aa3812b4ea053c43fdaa507a474a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042507"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="b2087-102">IMetaDataImport::EnumProperties – metoda</span><span class="sxs-lookup"><span data-stu-id="b2087-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="b2087-103">Vytvoří výčet vlastnosti tokeny představující vlastnosti typu odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b2087-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2087-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2087-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2087-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2087-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b2087-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b2087-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b2087-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="b2087-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="b2087-108">[in] Token TypeDef představující typ výčet s vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="b2087-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="b2087-109">[out] Pole pro ukládání tokenů vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2087-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b2087-110">[in] Maximální velikost `rProperties` pole.</span><span class="sxs-lookup"><span data-stu-id="b2087-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="b2087-111">[out] Počet tokenů vlastnosti vrácené v `rProperties`.</span><span class="sxs-lookup"><span data-stu-id="b2087-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2087-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b2087-112">Return Value</span></span>  
  
|<span data-ttu-id="b2087-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2087-113">HRESULT</span></span>|<span data-ttu-id="b2087-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b2087-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b2087-115">`EnumProperties` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b2087-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b2087-116">Neexistují žádné tokeny se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="b2087-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="b2087-117">V takovém případě `pcProperties` je nula.</span><span class="sxs-lookup"><span data-stu-id="b2087-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2087-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2087-118">Requirements</span></span>  
 <span data-ttu-id="b2087-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2087-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2087-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2087-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2087-121">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2087-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2087-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2087-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2087-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2087-123">See also</span></span>

- [<span data-ttu-id="b2087-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2087-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b2087-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2087-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
