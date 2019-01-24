---
title: IMetaDataImport::EnumFieldsWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 58c6e6685cc5c268d9313457469369d9df25e13b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564143"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="38077-102">IMetaDataImport::EnumFieldsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="38077-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="38077-103">Vytvoří výčet FieldDef tokeny zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="38077-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38077-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38077-104">Syntax</span></span>  
  
```  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]  mdTypeDef       cl,   
   [in]  LPCWSTR         szName,   
   [out] mdFieldDef      rFields[],   
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTokens   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38077-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38077-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="38077-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="38077-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="38077-107">[in] Token typu, jehož pole jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="38077-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="38077-108">[in] Název pole, která omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="38077-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="38077-109">[out] Pole pro ukládání tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="38077-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="38077-110">[in] Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="38077-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="38077-111">[out] Skutečný počet tokenů FieldDef vrácené v `rFields`.</span><span class="sxs-lookup"><span data-stu-id="38077-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38077-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38077-112">Remarks</span></span>  
 <span data-ttu-id="38077-113">Na rozdíl od [imetadataimport::enumfields –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` zahodí všechny tokeny pole, které nemají se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="38077-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38077-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="38077-114">Return Value</span></span>  
  
|<span data-ttu-id="38077-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38077-115">HRESULT</span></span>|<span data-ttu-id="38077-116">Popis</span><span class="sxs-lookup"><span data-stu-id="38077-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="38077-117">`EnumFieldsWithName` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="38077-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="38077-118">Nejsou žádná pole pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="38077-118">There are no fields to enumerate.</span></span> <span data-ttu-id="38077-119">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="38077-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="38077-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38077-120">Requirements</span></span>  
 <span data-ttu-id="38077-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38077-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38077-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38077-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38077-123">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="38077-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38077-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38077-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38077-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38077-125">See also</span></span>
- [<span data-ttu-id="38077-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38077-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="38077-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="38077-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
