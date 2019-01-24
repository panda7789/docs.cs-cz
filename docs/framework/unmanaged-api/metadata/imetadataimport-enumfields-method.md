---
title: IMetaDataImport::EnumFields – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4c16f904251545b87426210a76c5107e93a27749
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639559"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="7b8dc-102">IMetaDataImport::EnumFields – metoda</span><span class="sxs-lookup"><span data-stu-id="7b8dc-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="7b8dc-103">Vytvoří výčet FieldDef tokenů pro typ odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b8dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b8dc-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b8dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b8dc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7b8dc-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="7b8dc-107">[in] Token TypeDef třídy, jejichž pole jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="7b8dc-108">[out] Seznam tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7b8dc-109">[in] Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="7b8dc-110">[out] Skutečný počet tokenů FieldDef vrácené v `rFields`.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b8dc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7b8dc-111">Return Value</span></span>  
  
|<span data-ttu-id="7b8dc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b8dc-112">HRESULT</span></span>|<span data-ttu-id="7b8dc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7b8dc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7b8dc-114">`EnumFields` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7b8dc-115">Nejsou žádná pole pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-115">There are no fields to enumerate.</span></span> <span data-ttu-id="7b8dc-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="7b8dc-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7b8dc-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b8dc-117">Requirements</span></span>  
 <span data-ttu-id="7b8dc-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b8dc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b8dc-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7b8dc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b8dc-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b8dc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b8dc-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b8dc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b8dc-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b8dc-122">See also</span></span>
- [<span data-ttu-id="7b8dc-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b8dc-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7b8dc-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b8dc-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
