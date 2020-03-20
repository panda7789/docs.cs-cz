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
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175756"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="39c5f-102">IMetaDataEmit::DefineTypeDef – metoda</span><span class="sxs-lookup"><span data-stu-id="39c5f-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="39c5f-103">Vytvoří definici typu pro typ modulu runtime společného jazyka a získá token metadat pro tuto definici typu.</span><span class="sxs-lookup"><span data-stu-id="39c5f-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c5f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39c5f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39c5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="39c5f-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="39c5f-106">[v] Název typu v Unicode.</span><span class="sxs-lookup"><span data-stu-id="39c5f-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="39c5f-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="39c5f-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="39c5f-108">Toto je bitová maska `CoreTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="39c5f-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="39c5f-109">[v] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="39c5f-109">[in] The token of the base class.</span></span> <span data-ttu-id="39c5f-110">Musí být buď `mdTypeDef` token `mdTypeRef` nebo token.</span><span class="sxs-lookup"><span data-stu-id="39c5f-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="39c5f-111">[v] Pole tokenů určující rozhraní, které implementuje tato třída nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="39c5f-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="39c5f-112">[out] Přiřazen `mdTypeDef` token.</span><span class="sxs-lookup"><span data-stu-id="39c5f-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39c5f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39c5f-113">Remarks</span></span>  
 <span data-ttu-id="39c5f-114">Příznak v `dwTypeDefFlags` aplikaci určuje, zda je vytvářený typ běžným typem systému (třída nebo rozhraní) nebo běžným typem systémové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="39c5f-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="39c5f-115">V závislosti na zadaných parametrech může tato metoda jako `mdInterfaceImpl` vedlejší účinek také vytvořit záznam pro každé rozhraní, které je zděděno nebo implementováno tímto typem.</span><span class="sxs-lookup"><span data-stu-id="39c5f-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="39c5f-116">Tato metoda však nevrátí žádný `mdInterfaceImpl` z těchto tokenů.</span><span class="sxs-lookup"><span data-stu-id="39c5f-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="39c5f-117">Pokud klient chce později přidat `mdInterfaceImpl` nebo upravit token, musí použít `IMetaDataImport` rozhraní k jejich výčetu.</span><span class="sxs-lookup"><span data-stu-id="39c5f-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="39c5f-118">Pokud chcete použít sémantiku `[default]` com rozhraní, měli byste zadat výchozí `rtkImplements`rozhraní jako první prvek v ; vlastní atribut nastavený na třídě bude znamenat, že třída má výchozí `mdInterfaceImpl` rozhraní (což je vždy považováno za první token deklarovaný pro třídu).</span><span class="sxs-lookup"><span data-stu-id="39c5f-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="39c5f-119">Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` `mdTypeRef` nebo token.</span><span class="sxs-lookup"><span data-stu-id="39c5f-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="39c5f-120">Poslední prvek v poli `mdTokenNil`musí být .</span><span class="sxs-lookup"><span data-stu-id="39c5f-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c5f-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="39c5f-121">Requirements</span></span>  
 <span data-ttu-id="39c5f-122">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39c5f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c5f-123">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="39c5f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39c5f-124">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39c5f-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39c5f-125">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c5f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c5f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="39c5f-126">See also</span></span>

- [<span data-ttu-id="39c5f-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39c5f-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="39c5f-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="39c5f-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
