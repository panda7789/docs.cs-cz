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
ms.openlocfilehash: 54691785e3b2619b5f4a2eecc510800b4b5cee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446594"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="19397-102">IMetaDataEmit::DefineTypeDef – metoda</span><span class="sxs-lookup"><span data-stu-id="19397-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="19397-103">Vytvoří definici typu pro běžné typ modulu runtime jazyka a získá metadata token pro tuto definici typu.</span><span class="sxs-lookup"><span data-stu-id="19397-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19397-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19397-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19397-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19397-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="19397-106">[v] Název typu ve formátu Unicode.</span><span class="sxs-lookup"><span data-stu-id="19397-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="19397-107">[v] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="19397-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="19397-108">Toto je bitová maska s `CoreTypeAttr` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="19397-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="19397-109">[v] Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="19397-109">[in] The token of the base class.</span></span> <span data-ttu-id="19397-110">Musí být buď `mdTypeDef` nebo `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="19397-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="19397-111">[v] Pole určující rozhraní, která implementuje této třídě nebo rozhraní tokeny.</span><span class="sxs-lookup"><span data-stu-id="19397-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="19397-112">[out] `mdTypeDef` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="19397-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19397-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19397-113">Remarks</span></span>  
 <span data-ttu-id="19397-114">Příznak v `dwTypeDefFlags` Určuje, jestli je typ vytváří běžné typ systému typu odkazu (třídy nebo rozhraní) nebo společné typ hodnoty systému typu.</span><span class="sxs-lookup"><span data-stu-id="19397-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="19397-115">V závislosti na parametry zadané, tato metoda jako vedlejším účinkem, může taky vytvořit `mdInterfaceImpl` záznamu pro každý rozhraní, které je zděděná nebo implementované tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="19397-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="19397-116">Však tato metoda nevrátí žádné z těchto `mdInterfaceImpl` tokeny.</span><span class="sxs-lookup"><span data-stu-id="19397-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="19397-117">Pokud klient chce později přidat nebo upravit `mdInterfaceImpl` tokenu, musí používat `IMetaDataImport` rozhraní je výčet.</span><span class="sxs-lookup"><span data-stu-id="19397-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="19397-118">Pokud chcete použít sémantiku COM `[default]` rozhraní, musí zadat výchozí rozhraní jako prvním elementem v `rtkImplements`; vlastních atributů, nastavte u třídy bude znamenat, že třída má výchozí rozhraní (což je vždy předpokládá, že se nejprve `mdInterfaceImpl` token deklarovaný pro třídu).</span><span class="sxs-lookup"><span data-stu-id="19397-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="19397-119">Každý element `rtkImplements` pole blokování `mdTypeDef` nebo `mdTypeRef` tokenu.</span><span class="sxs-lookup"><span data-stu-id="19397-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="19397-120">Musí být posledním prvkem v poli `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="19397-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19397-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19397-121">Requirements</span></span>  
 <span data-ttu-id="19397-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19397-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19397-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19397-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19397-124">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19397-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19397-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19397-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19397-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="19397-126">See Also</span></span>  
 [<span data-ttu-id="19397-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19397-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="19397-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19397-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
