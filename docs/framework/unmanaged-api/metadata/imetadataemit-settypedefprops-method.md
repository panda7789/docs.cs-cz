---
title: IMetaDataEmit::SetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007764"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="c2528-102">IMetaDataEmit::SetTypeDefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c2528-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="c2528-103">Nastaví funkce typu definovaného předchozím voláním [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2528-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2528-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2528-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2528-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2528-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c2528-106">pro `mdTypeDef`Token získaný z původního volání [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2528-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="c2528-107">[in] `TypeDef` atribut.</span><span class="sxs-lookup"><span data-stu-id="c2528-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="c2528-108">Toto je Bitová maska `CorTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="c2528-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="c2528-109">pro `mdToken`Základní třída.</span><span class="sxs-lookup"><span data-stu-id="c2528-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="c2528-110">Získáno z předchozího volání [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md)nebo `null` .</span><span class="sxs-lookup"><span data-stu-id="c2528-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="c2528-111">pro Pole tokenů pro rozhraní, které tento typ implementuje.</span><span class="sxs-lookup"><span data-stu-id="c2528-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="c2528-112">Tyto `mdTypeRef` tokeny se získávají pomocí [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="c2528-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="c2528-113">Poslední prvek pole musí být `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="c2528-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2528-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2528-114">Requirements</span></span>  
 <span data-ttu-id="c2528-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2528-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2528-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c2528-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2528-117">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="c2528-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2528-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2528-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2528-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2528-119">See also</span></span>

- [<span data-ttu-id="c2528-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2528-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c2528-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2528-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
