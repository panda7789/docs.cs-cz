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
ms.openlocfilehash: b2ba46c025c2d031f0526c6a9da5f6ab07023741
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208446"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="e9868-102">IMetaDataImport::EnumEvents – metoda</span><span class="sxs-lookup"><span data-stu-id="e9868-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="e9868-103">Vytvoří výčet tokeny definice události pro konkrétní token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="e9868-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9868-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9868-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9868-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9868-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e9868-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e9868-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="e9868-107">[in] Token TypeDef jehož definice událostí jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="e9868-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="e9868-108">[out] Pole vrácené události.</span><span class="sxs-lookup"><span data-stu-id="e9868-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e9868-109">[in] Maximální velikost `rEvents` pole.</span><span class="sxs-lookup"><span data-stu-id="e9868-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="e9868-110">[out] Skutečný počet událostí vrácených v `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="e9868-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9868-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9868-111">Return Value</span></span>  
  
|<span data-ttu-id="e9868-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9868-112">HRESULT</span></span>|<span data-ttu-id="e9868-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e9868-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumEvents` <span data-ttu-id="e9868-114">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="e9868-114">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e9868-115">Nejsou žádné události k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="e9868-115">There are no events to enumerate.</span></span> <span data-ttu-id="e9868-116">V takovém případě `pcEvents` je nula.</span><span class="sxs-lookup"><span data-stu-id="e9868-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9868-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9868-117">Requirements</span></span>  
 <span data-ttu-id="e9868-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9868-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9868-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e9868-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9868-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9868-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e9868-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e9868-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9868-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9868-122">See also</span></span>

- [<span data-ttu-id="e9868-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9868-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e9868-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9868-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
