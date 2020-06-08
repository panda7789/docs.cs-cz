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
ms.openlocfilehash: 213cbd955e3d47a49abde579a54af48641e225ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491911"
---
# <a name="imetadataimportenummethodsemantics-method"></a><span data-ttu-id="2b8e9-102">IMetaDataImport::EnumMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="2b8e9-102">IMetaDataImport::EnumMethodSemantics Method</span></span>
<span data-ttu-id="2b8e9-103">Vytvoří výčet vlastností a událostí změny vlastností, na které se vztahuje zadaná metoda.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-103">Enumerates the properties and the property-change events to which the specified method is related.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b8e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b8e9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSemantics (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,
   [out] mdToken         rEventProp[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcEventProp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b8e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b8e9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2b8e9-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2b8e9-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="2b8e9-108">pro Token MethodDef omezující obor výčtu.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-108">[in] A MethodDef token that limits the scope of the enumeration.</span></span>  
  
 `rEventProp`  
 <span data-ttu-id="2b8e9-109">mimo Pole, které se používá k uložení událostí nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-109">[out] The array used to store the events or properties.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2b8e9-110">pro Maximální velikost `rEventProp` pole.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-110">[in] The maximum size of the `rEventProp` array.</span></span>  
  
 `pcEventProp`  
 <span data-ttu-id="2b8e9-111">mimo Počet událostí nebo vlastností vrácených v `rEventProp` .</span><span class="sxs-lookup"><span data-stu-id="2b8e9-111">[out] The number of events or properties returned in `rEventProp`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b8e9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b8e9-112">Return Value</span></span>  
  
|<span data-ttu-id="2b8e9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b8e9-113">HRESULT</span></span>|<span data-ttu-id="2b8e9-114">Description</span><span class="sxs-lookup"><span data-stu-id="2b8e9-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2b8e9-115">`EnumMethodSemantics`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-115">`EnumMethodSemantics` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2b8e9-116">Neexistují žádné události ani vlastnosti k zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-116">There are no events or properties to enumerate.</span></span> <span data-ttu-id="2b8e9-117">V takovém případě `pcEventProp` je nula.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-117">In that case, `pcEventProp` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b8e9-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b8e9-118">Remarks</span></span>  
 <span data-ttu-id="2b8e9-119">Mnoho typů modulu CLR (Common Language Runtime) definuje události *vlastností* `Changed` a `On` *Property* `Changed` metody vlastností týkající se jejich vlastností.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-119">Many common language runtime types define *Property*`Changed` events and `On`*Property*`Changed` methods related to their properties.</span></span> <span data-ttu-id="2b8e9-120"><xref:System.Windows.Forms.Control?displayProperty=nameWithType>Typ například definuje <xref:System.Windows.Forms.Control.Font%2A> vlastnost, <xref:System.Windows.Forms.Control.FontChanged> událost a <xref:System.Windows.Forms.Control.OnFontChanged%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-120">For example, the <xref:System.Windows.Forms.Control?displayProperty=nameWithType> type defines a <xref:System.Windows.Forms.Control.Font%2A> property, a <xref:System.Windows.Forms.Control.FontChanged> event, and an <xref:System.Windows.Forms.Control.OnFontChanged%2A> method.</span></span> <span data-ttu-id="2b8e9-121">Metoda set přistupující metody <xref:System.Windows.Forms.Control.Font%2A> volání vlastnosti <xref:System.Windows.Forms.Control.OnFontChanged%2A> , která vyvolá <xref:System.Windows.Forms.Control.FontChanged> událost.</span><span class="sxs-lookup"><span data-stu-id="2b8e9-121">The set accessor method of the <xref:System.Windows.Forms.Control.Font%2A> property calls <xref:System.Windows.Forms.Control.OnFontChanged%2A> method, which in turn raises the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span> <span data-ttu-id="2b8e9-122">`EnumMethodSemantics`Pro <xref:System.Windows.Forms.Control.OnFontChanged%2A> získání odkazů na <xref:System.Windows.Forms.Control.Font%2A> vlastnost a událost byste volali pomocí prvku MethodDef pro <xref:System.Windows.Forms.Control.FontChanged> .</span><span class="sxs-lookup"><span data-stu-id="2b8e9-122">You would call `EnumMethodSemantics` using the MethodDef for <xref:System.Windows.Forms.Control.OnFontChanged%2A> to get references to the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.Control.FontChanged> event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b8e9-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b8e9-123">Requirements</span></span>  
 <span data-ttu-id="2b8e9-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b8e9-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b8e9-125">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2b8e9-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b8e9-126">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b8e9-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b8e9-127">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b8e9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8e9-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b8e9-128">See also</span></span>

- [<span data-ttu-id="2b8e9-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b8e9-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2b8e9-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b8e9-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
