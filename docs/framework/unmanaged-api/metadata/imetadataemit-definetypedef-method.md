---
title: IMetaDataEmit::DefineTypeDef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf2ca9719cdf62637292bdb39437d36f4b3fcd49
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494401"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="e83b9-102">IMetaDataEmit::DefineTypeDef – metoda</span><span class="sxs-lookup"><span data-stu-id="e83b9-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="e83b9-103">Vytvoří definici typu pro společný typ modulu runtime jazyka a získá token metadat pro tuto definici typu.</span><span class="sxs-lookup"><span data-stu-id="e83b9-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e83b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e83b9-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e83b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e83b9-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="e83b9-106">[in] Název typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="e83b9-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="e83b9-107">[in] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="e83b9-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="e83b9-108">To je bitová maska z `CoreTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e83b9-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="e83b9-109">[in] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e83b9-109">[in] The token of the base class.</span></span> <span data-ttu-id="e83b9-110">Musí se jednat buď `mdTypeDef` nebo `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="e83b9-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="e83b9-111">[in] Pole tokeny zadání rozhraní, které implementuje Tato třída nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e83b9-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="e83b9-112">[out] `mdTypeDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="e83b9-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e83b9-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e83b9-113">Remarks</span></span>  
 <span data-ttu-id="e83b9-114">Příznak v `dwTypeDefFlags` Určuje, zda je typ vytváří společný typ systému typem odkazu (třídy nebo rozhraní) nebo na společný typ. hodnota typu systému.</span><span class="sxs-lookup"><span data-stu-id="e83b9-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="e83b9-115">V závislosti na zadaných parametrů této metody jako vedlejší účinek, může také vytvořit `mdInterfaceImpl` záznamů pro každé rozhraní, které je zděděná nebo implementovaný tímto typem.</span><span class="sxs-lookup"><span data-stu-id="e83b9-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="e83b9-116">Ale tato metoda nevrátí žádnou z těchto `mdInterfaceImpl` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e83b9-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="e83b9-117">Pokud klient požaduje později přidat nebo upravit `mdInterfaceImpl` tokenu, je nutné použít `IMetaDataImport` rozhraní je výčet.</span><span class="sxs-lookup"><span data-stu-id="e83b9-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="e83b9-118">Pokud chcete použít sémantika COM `[default]` rozhraní, by mělo nabízet výchozí rozhraní jako první prvek v `rtkImplements`; vlastní atribut nastaven na třídy bude označovat, že třída nemá výchozí rozhraní (což je vždy považován za nejprve `mdInterfaceImpl` token deklarované třídy).</span><span class="sxs-lookup"><span data-stu-id="e83b9-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="e83b9-119">Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` nebo `mdTypeRef` token.</span><span class="sxs-lookup"><span data-stu-id="e83b9-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="e83b9-120">Poslední prvek v poli musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="e83b9-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e83b9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e83b9-121">Requirements</span></span>  
 <span data-ttu-id="e83b9-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e83b9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e83b9-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e83b9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e83b9-124">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e83b9-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e83b9-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e83b9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e83b9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e83b9-126">See also</span></span>
- [<span data-ttu-id="e83b9-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e83b9-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e83b9-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e83b9-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
