---
title: "IMetaDataEmit::SetClassLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0c02e615bf77a2cc9136b50efd7395585959141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="5d3a4-102">IMetaDataEmit::SetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="5d3a4-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="5d3a4-103">Dokončení rozložení polí pro třídu, která byla definována voláním předchozí [definetypedef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d3a4-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d3a4-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d3a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d3a4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5d3a4-106">[v] `mdTypeDef` Token, který určuje třídy pro rozloženy.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="5d3a4-107">[v] Velikost okolních: 1, 2, 4, 8 nebo 16 bajtů.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="5d3a4-108">Velikost okolních je počet bajtů mezi sousedící pole.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="5d3a4-109">[v] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý určuje pole třídy a pole Posun v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="5d3a4-110">Ukončit pole s `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="5d3a4-111">[v] Velikost v bajtech, třídy.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d3a4-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d3a4-112">Remarks</span></span>  
 <span data-ttu-id="5d3a4-113">Je třída definovaná původně voláním [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metoda a zadáním jednoho z tři rozložení pro pole třídy: automaticky, sekvenční nebo explicitní.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="5d3a4-114">Za normálních okolností byste pomocí automatického rozložení a dát modulu runtime, zvolte nejlepší způsob, jak rozložení polí.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="5d3a4-115">Ale můžete chtít pole nastíněny podle uspořádání, který nespravovaného kódu používá.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="5d3a4-116">V takovém případě zvolte sekvenční nebo explicitní rozložení a volání `SetClassLayout` k dokončení rozložení polí:</span><span class="sxs-lookup"><span data-stu-id="5d3a4-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="5d3a4-117">Sekvenční rozložení: Zadejte velikost okolních.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="5d3a4-118">Pole je zarovnán podle jeho přirozené velikost nebo okolních velikostí, podle toho, která má za následek menší posun pole.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="5d3a4-119">Nastavit `rFieldOffsets` a `ulClassSize` na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="5d3a4-120">Explicitní rozložení: posun každého pole nebo zadejte velikost třídy a okolních velikost.</span><span class="sxs-lookup"><span data-stu-id="5d3a4-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d3a4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d3a4-121">Requirements</span></span>  
 <span data-ttu-id="5d3a4-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d3a4-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d3a4-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d3a4-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d3a4-124">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5d3a4-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d3a4-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d3a4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3a4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d3a4-126">See Also</span></span>  
 [<span data-ttu-id="5d3a4-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d3a4-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5d3a4-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d3a4-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
