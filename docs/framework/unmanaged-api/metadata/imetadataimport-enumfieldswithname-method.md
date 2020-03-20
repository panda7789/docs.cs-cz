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
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177345"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="c2bc0-102">IMetaDataImport::EnumFieldsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="c2bc0-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="c2bc0-103">Vyjmenovává tokeny FieldDef zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2bc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2bc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2bc0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c2bc0-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c2bc0-107">[v] Token typu, jehož pole mají být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="c2bc0-108">[v] Název pole, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="c2bc0-109">[out] Pole používané k ukládání tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c2bc0-110">[v] Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c2bc0-111">[out] Skutečný počet tokenů FieldDef `rFields`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="c2bc0-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2bc0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2bc0-112">Remarks</span></span>  
 <span data-ttu-id="c2bc0-113">Na rozdíl od [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` zahodí všechny tokeny polí, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2bc0-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c2bc0-114">Return Value</span></span>  
  
|<span data-ttu-id="c2bc0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2bc0-115">HRESULT</span></span>|<span data-ttu-id="c2bc0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c2bc0-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c2bc0-117">`EnumFieldsWithName`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c2bc0-118">Neexistují žádná pole, která by bylo možné vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-118">There are no fields to enumerate.</span></span> <span data-ttu-id="c2bc0-119">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2bc0-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2bc0-120">Requirements</span></span>  
 <span data-ttu-id="c2bc0-121">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2bc0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2bc0-122">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c2bc0-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2bc0-123">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2bc0-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2bc0-124">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2bc0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2bc0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2bc0-125">See also</span></span>

- [<span data-ttu-id="c2bc0-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2bc0-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c2bc0-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2bc0-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
