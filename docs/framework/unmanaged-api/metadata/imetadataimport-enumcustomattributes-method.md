---
title: IMetaDataImport::EnumCustomAttributes – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175522"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="c1df8-102">IMetaDataImport::EnumCustomAttributes – metoda</span><span class="sxs-lookup"><span data-stu-id="c1df8-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="c1df8-103">Vyjmenovává tokeny vlastní definice atributu přidružené k zadanému typu nebo členu.</span><span class="sxs-lookup"><span data-stu-id="c1df8-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1df8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1df8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1df8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1df8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c1df8-106">[dovnitř, ven] Ukazatel na vrácený čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="c1df8-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="c1df8-107">[v] Token pro rozsah výčtu nebo nula pro všechny vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="c1df8-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="c1df8-108">[v] Token pro konstruktor typu atributů, které mají být uvedeny `null` ve výčtu, nebo pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="c1df8-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="c1df8-109">[out] Pole tokenů vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="c1df8-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c1df8-110">[v] Maximální velikost `rCustomAttributes` pole.</span><span class="sxs-lookup"><span data-stu-id="c1df8-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="c1df8-111">[ven, nepovinné] Skutečný počet hodnot tokenu `rCustomAttributes`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="c1df8-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1df8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c1df8-112">Return Value</span></span>  
  
|<span data-ttu-id="c1df8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1df8-113">HRESULT</span></span>|<span data-ttu-id="c1df8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c1df8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1df8-115">`EnumCustomAttributes`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c1df8-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c1df8-116">Neexistují žádné vlastní atributy výčet.</span><span class="sxs-lookup"><span data-stu-id="c1df8-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="c1df8-117">V tom `pcCustomAttributes` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="c1df8-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1df8-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1df8-118">Requirements</span></span>  
 <span data-ttu-id="c1df8-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1df8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1df8-120">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="c1df8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1df8-121">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1df8-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1df8-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1df8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1df8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1df8-123">See also</span></span>

- [<span data-ttu-id="c1df8-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1df8-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c1df8-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1df8-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
