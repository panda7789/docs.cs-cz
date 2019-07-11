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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 715e53ae04532214d4011d4a40503b2ade5a014d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782077"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="95bf8-102">IMetaDataImport::EnumMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="95bf8-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="95bf8-103">Vytvoří výčet vlastností a změnu vlastnosti události, ke kterým se vztahuje zadanou metodu.</span><span class="sxs-lookup"><span data-stu-id="95bf8-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95bf8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95bf8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,   
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95bf8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95bf8-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="95bf8-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="95bf8-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="95bf8-107">První volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="95bf8-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="95bf8-108">[in] Token MethodDef, která omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="95bf8-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="95bf8-109">[out] Pole používá k ukládání vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="95bf8-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="95bf8-110">[in] Maximální velikost `rEventProp` pole.</span><span class="sxs-lookup"><span data-stu-id="95bf8-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="95bf8-111">[out] Počet událostí nebo vlastnosti, které jsou vráceny v `rEventProp`.</span><span class="sxs-lookup"><span data-stu-id="95bf8-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95bf8-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95bf8-112">Return Value</span></span>  
  
|<span data-ttu-id="95bf8-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95bf8-113">HRESULT</span></span>|<span data-ttu-id="95bf8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="95bf8-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="95bf8-115">`EnumMethodSemantics` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="95bf8-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="95bf8-116">Neexistují žádné události nebo vlastnosti, které chcete zobrazit výčet.</span><span class="sxs-lookup"><span data-stu-id="95bf8-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="95bf8-117">V takovém případě `pcEventProp` je nula.</span><span class="sxs-lookup"><span data-stu-id="95bf8-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95bf8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95bf8-118">Remarks</span></span>  
 <span data-ttu-id="95bf8-119">Mnoho běžných typů modulu runtime jazyka definovat *vlastnost* `Changed` události a `On` *vlastnost* `Changed` metody související s jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="95bf8-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="95bf8-120">Například <xref:System.Windows.Forms.Control?displayProperty=nameWithType> definuje typ <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> události a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="95bf8-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="95bf8-121">Metodu přístupového objektu set <xref:System.Windows.Forms.Control.Font%2A> vlastnost volání <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu, která postupně vyvolá <xref:System.Windows.Forms.Control.FontChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="95bf8-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="95bf8-122">By volat `EnumMethodSemantics` pomocí MethodDef pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> zobrazíte odkazy na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.Control.FontChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="95bf8-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95bf8-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95bf8-123">Requirements</span></span>  
 <span data-ttu-id="95bf8-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95bf8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95bf8-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95bf8-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95bf8-126">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95bf8-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95bf8-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95bf8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95bf8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95bf8-128">See also</span></span>

- [<span data-ttu-id="95bf8-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95bf8-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="95bf8-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95bf8-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
