---
title: IMetaDataImport::EnumTypeRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503741"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="bd10f-102">IMetaDataImport::EnumTypeRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="bd10f-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="bd10f-103">Vytvoří výčet tokenů TypeRef definovaných v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="bd10f-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd10f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd10f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd10f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd10f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bd10f-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="bd10f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bd10f-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="bd10f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="bd10f-108">mimo Pole použité pro uložení tokenů TypeRef</span><span class="sxs-lookup"><span data-stu-id="bd10f-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bd10f-109">pro Maximální velikost `rTypeRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="bd10f-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="bd10f-110">mimo Ukazatel na počet vrácených tokenů TypeRef `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="bd10f-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd10f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd10f-111">Return Value</span></span>  
  
|<span data-ttu-id="bd10f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd10f-112">HRESULT</span></span>|<span data-ttu-id="bd10f-113">Description</span><span class="sxs-lookup"><span data-stu-id="bd10f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bd10f-114">`EnumTypeRefs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="bd10f-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bd10f-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="bd10f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="bd10f-116">V takovém případě `pcTypeRefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="bd10f-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd10f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd10f-117">Remarks</span></span>  
 <span data-ttu-id="bd10f-118">Token TypeRef představuje odkaz na typ.</span><span class="sxs-lookup"><span data-stu-id="bd10f-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd10f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd10f-119">Requirements</span></span>  
 <span data-ttu-id="bd10f-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd10f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd10f-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bd10f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd10f-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd10f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd10f-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd10f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd10f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd10f-124">See also</span></span>

- [<span data-ttu-id="bd10f-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd10f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="bd10f-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd10f-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
