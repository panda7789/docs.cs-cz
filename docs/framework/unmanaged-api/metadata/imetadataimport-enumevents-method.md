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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 608b4a7d147124ede60e9d81f91600dfdaad0a65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446493"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="a388b-102">IMetaDataImport::EnumEvents – metoda</span><span class="sxs-lookup"><span data-stu-id="a388b-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="a388b-103">Vytvoří výčet událostí definice tokeny pro zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="a388b-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a388b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a388b-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a388b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a388b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a388b-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a388b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="a388b-107">[v] Token TypeDef, jejichž definice událostí jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="a388b-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="a388b-108">[out] Pole vrácené události.</span><span class="sxs-lookup"><span data-stu-id="a388b-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a388b-109">[v] Maximální velikost `rEvents` pole.</span><span class="sxs-lookup"><span data-stu-id="a388b-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="a388b-110">[out] Skutečný počet událostí vrácených v `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="a388b-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a388b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a388b-111">Return Value</span></span>  
  
|<span data-ttu-id="a388b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a388b-112">HRESULT</span></span>|<span data-ttu-id="a388b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a388b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a388b-114">`EnumEvents` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a388b-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a388b-115">Nejsou k dispozici žádné události k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="a388b-115">There are no events to enumerate.</span></span> <span data-ttu-id="a388b-116">V takovém případě `pcEvents` je nulová.</span><span class="sxs-lookup"><span data-stu-id="a388b-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a388b-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a388b-117">Requirements</span></span>  
 <span data-ttu-id="a388b-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a388b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a388b-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a388b-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a388b-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a388b-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a388b-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a388b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a388b-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a388b-122">See Also</span></span>  
 [<span data-ttu-id="a388b-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a388b-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a388b-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a388b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
