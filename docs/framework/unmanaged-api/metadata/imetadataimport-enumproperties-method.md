---
title: IMetaDataImport::EnumProperties – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 39343ffc88fc9b421b916e33e3e75e4e34fc233d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503788"
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="27882-102">IMetaDataImport::EnumProperties – metoda</span><span class="sxs-lookup"><span data-stu-id="27882-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="27882-103">Vytvoří výčet tokenů PropertyDef představujících vlastnosti typu, na který odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="27882-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27882-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27882-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27882-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27882-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="27882-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="27882-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="27882-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="27882-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="27882-108">pro Token TypeDef představující typ s vlastnostmi k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="27882-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="27882-109">mimo Pole, které se používá k uložení tokenů PropertyDef.</span><span class="sxs-lookup"><span data-stu-id="27882-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="27882-110">pro Maximální velikost `rProperties` pole.</span><span class="sxs-lookup"><span data-stu-id="27882-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="27882-111">mimo Počet vrácených tokenů PropertyDef `rProperties` .</span><span class="sxs-lookup"><span data-stu-id="27882-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27882-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="27882-112">Return Value</span></span>  
  
|<span data-ttu-id="27882-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27882-113">HRESULT</span></span>|<span data-ttu-id="27882-114">Description</span><span class="sxs-lookup"><span data-stu-id="27882-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="27882-115">`EnumProperties`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="27882-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="27882-116">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="27882-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="27882-117">V takovém případě `pcProperties` je nula.</span><span class="sxs-lookup"><span data-stu-id="27882-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27882-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27882-118">Requirements</span></span>  
 <span data-ttu-id="27882-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27882-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27882-120">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="27882-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="27882-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="27882-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27882-122">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27882-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27882-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27882-123">See also</span></span>

- [<span data-ttu-id="27882-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27882-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="27882-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27882-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
