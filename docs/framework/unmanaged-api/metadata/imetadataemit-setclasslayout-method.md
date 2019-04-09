---
title: IMetaDataEmit::SetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157700"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="48f5e-102">IMetaDataEmit::SetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="48f5e-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="48f5e-103">Dokončení rozložení polí pro třídu, která je definována v předchozím volání [definetypedef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="48f5e-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48f5e-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48f5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="48f5e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="48f5e-106">[in] `mdTypeDef` Token, který určuje třídy, která se vytvoří rozložení.</span><span class="sxs-lookup"><span data-stu-id="48f5e-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="48f5e-107">[in] Velikost komprimace: 1, 2, 4, 8 nebo 16 bajtů.</span><span class="sxs-lookup"><span data-stu-id="48f5e-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="48f5e-108">Počet bajtů mezi sousedící pole je velikost komprimace.</span><span class="sxs-lookup"><span data-stu-id="48f5e-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="48f5e-109">[in] Pole [cor_field_offset –](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z nichž každý určuje pole třídy a posun v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="48f5e-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="48f5e-110">Ukončit pole s `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="48f5e-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="48f5e-111">[in] Velikost v bajtech třídy.</span><span class="sxs-lookup"><span data-stu-id="48f5e-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48f5e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48f5e-112">Remarks</span></span>  
 <span data-ttu-id="48f5e-113">Zpočátku je třída definovaná pomocí volání [imetadataemit::definetypedef –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metoda a zadáním jednoho z tři rozložení pro pole třídy: automaticky, sekvenční nebo explicitní.</span><span class="sxs-lookup"><span data-stu-id="48f5e-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="48f5e-114">Za normálních okolností byste pomocí automatického rozložení a umožní modulu runtime, zvolte nejlepší způsob, jak rozložení polí.</span><span class="sxs-lookup"><span data-stu-id="48f5e-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="48f5e-115">Však můžete chtít pole neuplatní uspořádání nespravovaný kód používá.</span><span class="sxs-lookup"><span data-stu-id="48f5e-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="48f5e-116">V tomto případě zvolte sekvenční nebo explicitní rozložení a volání `SetClassLayout` dokončete rozložení polí:</span><span class="sxs-lookup"><span data-stu-id="48f5e-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="48f5e-117">Sekvenční rozložení: Zadejte velikost komprimace.</span><span class="sxs-lookup"><span data-stu-id="48f5e-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="48f5e-118">Pole je zarovnán podle jeho fyzické velikosti nebo velikosti komprimace, podle toho, která má za následek menší posun pole.</span><span class="sxs-lookup"><span data-stu-id="48f5e-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="48f5e-119">Nastavte `rFieldOffsets` a `ulClassSize` na nulu.</span><span class="sxs-lookup"><span data-stu-id="48f5e-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="48f5e-120">Explicitní rozložení: Zadejte posun každé pole nebo určit třídu velikost a velikost komprimace.</span><span class="sxs-lookup"><span data-stu-id="48f5e-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48f5e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48f5e-121">Requirements</span></span>  
 <span data-ttu-id="48f5e-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48f5e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48f5e-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="48f5e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48f5e-124">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48f5e-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="48f5e-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="48f5e-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="48f5e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="48f5e-126">See also</span></span>

- [<span data-ttu-id="48f5e-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48f5e-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="48f5e-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="48f5e-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
