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
ms.openlocfilehash: be2845d1d660d86447cfbb6f2845a8e68b727e66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175509"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="399b8-102">IMetaDataImport::EnumFields – metoda</span><span class="sxs-lookup"><span data-stu-id="399b8-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="399b8-103">Zároveň vyjmenovává tokeny FieldDef pro typ odkazovaný zadaným tokenem TypeDef.</span><span class="sxs-lookup"><span data-stu-id="399b8-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="399b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="399b8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="399b8-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="399b8-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="399b8-107">[v] TypeDef token třídy, jejíž pole mají být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="399b8-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="399b8-108">[out] Seznam tokenů FieldDef.</span><span class="sxs-lookup"><span data-stu-id="399b8-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="399b8-109">[v] Maximální velikost `rFields` pole.</span><span class="sxs-lookup"><span data-stu-id="399b8-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="399b8-110">[out] Skutečný počet tokenů FieldDef `rFields`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="399b8-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="399b8-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="399b8-111">Return Value</span></span>  
  
|<span data-ttu-id="399b8-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="399b8-112">HRESULT</span></span>|<span data-ttu-id="399b8-113">Popis</span><span class="sxs-lookup"><span data-stu-id="399b8-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="399b8-114">`EnumFields`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="399b8-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="399b8-115">Neexistují žádná pole, která by bylo možné vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="399b8-115">There are no fields to enumerate.</span></span> <span data-ttu-id="399b8-116">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="399b8-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="399b8-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="399b8-117">Requirements</span></span>  
 <span data-ttu-id="399b8-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="399b8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="399b8-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="399b8-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="399b8-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="399b8-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="399b8-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="399b8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399b8-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="399b8-122">See also</span></span>

- [<span data-ttu-id="399b8-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="399b8-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="399b8-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="399b8-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
