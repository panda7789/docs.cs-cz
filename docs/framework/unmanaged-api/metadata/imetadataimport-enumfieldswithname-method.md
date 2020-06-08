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
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492262"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="c08d5-102">IMetaDataImport::EnumFieldsWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="c08d5-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="c08d5-103">Vytvoří výčet tokenů FieldDef zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="c08d5-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c08d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c08d5-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c08d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c08d5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c08d5-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="c08d5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c08d5-107">pro Token typu, jehož pole se mají vyčíslit</span><span class="sxs-lookup"><span data-stu-id="c08d5-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="c08d5-108">pro Název pole, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="c08d5-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="c08d5-109">mimo Pole, které se používá k uložení tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="c08d5-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c08d5-110">pro Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="c08d5-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c08d5-111">mimo Skutečný počet FieldDef tokenů vrácených v `rFields` .</span><span class="sxs-lookup"><span data-stu-id="c08d5-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c08d5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c08d5-112">Remarks</span></span>  
 <span data-ttu-id="c08d5-113">Na rozdíl od [IMetaDataImport:: enumfields –](imetadataimport-enumfields-method.md) `EnumFieldsWithName` zahodí všechny tokeny pole, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="c08d5-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c08d5-114">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c08d5-114">Return Value</span></span>  
  
|<span data-ttu-id="c08d5-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c08d5-115">HRESULT</span></span>|<span data-ttu-id="c08d5-116">Description</span><span class="sxs-lookup"><span data-stu-id="c08d5-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c08d5-117">`EnumFieldsWithName`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c08d5-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c08d5-118">Neexistují žádná pole k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="c08d5-118">There are no fields to enumerate.</span></span> <span data-ttu-id="c08d5-119">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="c08d5-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c08d5-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c08d5-120">Requirements</span></span>  
 <span data-ttu-id="c08d5-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c08d5-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08d5-122">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c08d5-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c08d5-123">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c08d5-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c08d5-124">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c08d5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08d5-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c08d5-125">See also</span></span>

- [<span data-ttu-id="c08d5-126">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c08d5-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c08d5-127">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c08d5-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
