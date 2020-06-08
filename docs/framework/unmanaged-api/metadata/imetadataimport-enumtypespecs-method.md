---
title: IMetaDataImport::EnumTypeSpecs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503715"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="6470f-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="6470f-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="6470f-103">Vytvoří výčet tokenů token TypeSpec definovaných v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="6470f-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6470f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6470f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6470f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6470f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6470f-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6470f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6470f-107">Tato hodnota musí být pro první volání této metody NULL.</span><span class="sxs-lookup"><span data-stu-id="6470f-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="6470f-108">mimo Pole, které se používá k uložení tokenů token TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="6470f-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6470f-109">pro Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="6470f-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="6470f-110">mimo Počet vrácených tokenů token TypeSpec `rTypeSpecs` .</span><span class="sxs-lookup"><span data-stu-id="6470f-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6470f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6470f-111">Return Value</span></span>  
  
|<span data-ttu-id="6470f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6470f-112">HRESULT</span></span>|<span data-ttu-id="6470f-113">Description</span><span class="sxs-lookup"><span data-stu-id="6470f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6470f-114">`EnumTypeSpecs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6470f-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6470f-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="6470f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6470f-116">V takovém případě `pcTypeSpecs` je nula.</span><span class="sxs-lookup"><span data-stu-id="6470f-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6470f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6470f-117">Remarks</span></span>  
 <span data-ttu-id="6470f-118">Tokeny token TypeSpec jsou vytvořeny metodou [IMetaDataEmit:: gettokenfromtypespec –](imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6470f-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6470f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6470f-119">Requirements</span></span>  
 <span data-ttu-id="6470f-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6470f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6470f-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6470f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6470f-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6470f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6470f-123">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6470f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6470f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6470f-124">See also</span></span>

- [<span data-ttu-id="6470f-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6470f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6470f-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6470f-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
