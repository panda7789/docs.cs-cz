---
title: IMetaDataImport::EnumEvents – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: bd50d63b1f7080f510c29f90979b7b36242af1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177375"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="d6015-102">IMetaDataImport::EnumEvents – metoda</span><span class="sxs-lookup"><span data-stu-id="d6015-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="d6015-103">Vyjmenovává tokeny definice události pro zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="d6015-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6015-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6015-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6015-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6015-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d6015-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="d6015-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="d6015-107">[v] TypeDef token, jehož definice událostí mají být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="d6015-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="d6015-108">[out] Pole vrácené události.</span><span class="sxs-lookup"><span data-stu-id="d6015-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d6015-109">[v] Maximální velikost `rEvents` pole.</span><span class="sxs-lookup"><span data-stu-id="d6015-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="d6015-110">[out] Skutečný počet vrácených `rEvents`událostí v .</span><span class="sxs-lookup"><span data-stu-id="d6015-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6015-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d6015-111">Return Value</span></span>  
  
|<span data-ttu-id="d6015-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6015-112">HRESULT</span></span>|<span data-ttu-id="d6015-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d6015-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6015-114">`EnumEvents`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d6015-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d6015-115">Neexistují žádné události výčet.</span><span class="sxs-lookup"><span data-stu-id="d6015-115">There are no events to enumerate.</span></span> <span data-ttu-id="d6015-116">V tom `pcEvents` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="d6015-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6015-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6015-117">Requirements</span></span>  
 <span data-ttu-id="d6015-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6015-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6015-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d6015-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6015-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6015-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6015-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6015-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6015-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6015-122">See also</span></span>

- [<span data-ttu-id="d6015-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6015-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d6015-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6015-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
