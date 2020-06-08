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
ms.openlocfilehash: 53b1234a176cade5876d70da0cb4eadc18802c69
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492301"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="952fe-102">IMetaDataImport::EnumEvents – metoda</span><span class="sxs-lookup"><span data-stu-id="952fe-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="952fe-103">Vytvoří výčet tokenů definice události pro zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="952fe-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="952fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="952fe-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="952fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="952fe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="952fe-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="952fe-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="952fe-107">pro Token TypeDef, jehož definice událostí mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="952fe-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="952fe-108">mimo Pole vrácených událostí</span><span class="sxs-lookup"><span data-stu-id="952fe-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="952fe-109">pro Maximální velikost `rEvents` pole.</span><span class="sxs-lookup"><span data-stu-id="952fe-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="952fe-110">mimo Skutečný počet událostí vrácených v `rEvents` .</span><span class="sxs-lookup"><span data-stu-id="952fe-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="952fe-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="952fe-111">Return Value</span></span>  
  
|<span data-ttu-id="952fe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="952fe-112">HRESULT</span></span>|<span data-ttu-id="952fe-113">Description</span><span class="sxs-lookup"><span data-stu-id="952fe-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="952fe-114">`EnumEvents`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="952fe-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="952fe-115">Nejsou k dispozici žádné události k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="952fe-115">There are no events to enumerate.</span></span> <span data-ttu-id="952fe-116">V takovém případě `pcEvents` je nula.</span><span class="sxs-lookup"><span data-stu-id="952fe-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="952fe-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="952fe-117">Requirements</span></span>  
 <span data-ttu-id="952fe-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="952fe-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="952fe-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="952fe-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="952fe-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="952fe-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="952fe-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="952fe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="952fe-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="952fe-122">See also</span></span>

- [<span data-ttu-id="952fe-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="952fe-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="952fe-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="952fe-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
