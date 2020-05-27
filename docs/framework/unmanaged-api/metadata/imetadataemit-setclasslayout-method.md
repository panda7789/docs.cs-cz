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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008825"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="52e21-102">IMetaDataEmit::SetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="52e21-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="52e21-103">Dokončí rozložení polí pro třídu, která byla definována před voláním [metody definetypedef –](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="52e21-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52e21-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52e21-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52e21-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="52e21-106">pro `mdTypeDef`Token, který určuje třídu, která má být rozložena.</span><span class="sxs-lookup"><span data-stu-id="52e21-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="52e21-107">pro Velikost balení: 1, 2, 4, 8 nebo 16 bajtů.</span><span class="sxs-lookup"><span data-stu-id="52e21-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="52e21-108">Velikost balení je počet bajtů mezi sousedními poli.</span><span class="sxs-lookup"><span data-stu-id="52e21-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="52e21-109">pro Pole struktur [COR_FIELD_OFFSET](cor-field-offset-structure.md) , z nichž každý určuje pole třídy a posun pole v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="52e21-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="52e21-110">Pole ukončete pomocí `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="52e21-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="52e21-111">pro Velikost třídy (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="52e21-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52e21-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52e21-112">Remarks</span></span>  
 <span data-ttu-id="52e21-113">Třída je zpočátku definována voláním metody [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md) a zadáním jednoho ze tří rozložení pro pole třídy: Automatic, sekvenční nebo Explicit.</span><span class="sxs-lookup"><span data-stu-id="52e21-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="52e21-114">Normálně byste použili automatické rozložení a umožnili modulu runtime zvolit nejlepší způsob rozložení polí.</span><span class="sxs-lookup"><span data-stu-id="52e21-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="52e21-115">Můžete však chtít, aby pole byla rozložena podle uspořádání, které používá nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="52e21-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="52e21-116">V takovém případě vyberte buď sekvenční nebo explicitní rozložení, a volání `SetClassLayout` pro dokončení rozložení polí:</span><span class="sxs-lookup"><span data-stu-id="52e21-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="52e21-117">Sekvenční rozložení: Určete velikost balení.</span><span class="sxs-lookup"><span data-stu-id="52e21-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="52e21-118">Pole je zarovnáno podle jeho přirozené velikosti nebo velikosti balení, podle toho, co je výsledkem menšího posunu pole.</span><span class="sxs-lookup"><span data-stu-id="52e21-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="52e21-119">Nastavte `rFieldOffsets` a `ulClassSize` na nula.</span><span class="sxs-lookup"><span data-stu-id="52e21-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="52e21-120">Explicitní rozložení: buď zadejte posunutí jednotlivých polí, nebo zadejte velikost třídy a velikost balení.</span><span class="sxs-lookup"><span data-stu-id="52e21-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e21-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52e21-121">Requirements</span></span>  
 <span data-ttu-id="52e21-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e21-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e21-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="52e21-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52e21-124">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="52e21-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52e21-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e21-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e21-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="52e21-126">See also</span></span>

- [<span data-ttu-id="52e21-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52e21-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="52e21-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52e21-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
