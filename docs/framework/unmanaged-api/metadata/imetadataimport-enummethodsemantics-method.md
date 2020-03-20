---
title: IMetaDataImport::EnumMethodSemantics – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodSemantics
helpviewer_keywords:
- EnumMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::EnumMethodSemantics method [.NET Framework metadata]
ms.assetid: e7e3c630-9691-46d6-94df-b5593a7bb08a
topic_type:
- apiref
ms.openlocfilehash: f20652a7f86576e64646a1f63c3e2c48b55cf811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175457"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="06414-102">IMetaDataImport::EnumMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="06414-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="06414-103">Výčet vlastností a událostí změny vlastnosti, ke kterým se vztahuje zadaná metoda.</span><span class="sxs-lookup"><span data-stu-id="06414-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06414-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06414-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06414-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06414-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="06414-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="06414-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="06414-107">To musí být NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="06414-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="06414-108">[v] A MethodDef token, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="06414-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="06414-109">[out] Pole používané k uložení událostí nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="06414-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="06414-110">[v] Maximální velikost `rEventProp` pole.</span><span class="sxs-lookup"><span data-stu-id="06414-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="06414-111">[out] Počet událostí nebo vlastností `rEventProp`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="06414-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06414-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06414-112">Return Value</span></span>  
  
|<span data-ttu-id="06414-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06414-113">HRESULT</span></span>|<span data-ttu-id="06414-114">Popis</span><span class="sxs-lookup"><span data-stu-id="06414-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="06414-115">`EnumMethodSemantics`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="06414-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="06414-116">Neexistují žádné události nebo vlastnosti výčet.</span><span class="sxs-lookup"><span data-stu-id="06414-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="06414-117">V tom `pcEventProp` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="06414-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06414-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06414-118">Remarks</span></span>  
 <span data-ttu-id="06414-119">Mnoho běžných typů běhového `On`času jazyka definuje události *vlastností* `Changed` a metody *property* `Changed` související s jejich vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="06414-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="06414-120">Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> typ definuje <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> událost a metodu. <xref:System.Windows.Forms.Control.OnFontChanged%2A></span><span class="sxs-lookup"><span data-stu-id="06414-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="06414-121">Set přistupující <xref:System.Windows.Forms.Control.Font%2A> metoda <xref:System.Windows.Forms.Control.OnFontChanged%2A> vlastnostvolá metodu, <xref:System.Windows.Forms.Control.FontChanged> která zase vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="06414-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="06414-122">Byste volat `EnumMethodSemantics` pomocí MethodDef <xref:System.Windows.Forms.Control.OnFontChanged%2A> pro získat odkazy <xref:System.Windows.Forms.Control.Font%2A> na <xref:System.Windows.Forms.Control.FontChanged> vlastnost a událost.</span><span class="sxs-lookup"><span data-stu-id="06414-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06414-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06414-123">Requirements</span></span>  
 <span data-ttu-id="06414-124">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06414-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06414-125">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="06414-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06414-126">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06414-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06414-127">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06414-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06414-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="06414-128">See also</span></span>

- [<span data-ttu-id="06414-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06414-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="06414-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06414-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
