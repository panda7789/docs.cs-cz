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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450211"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="bcfc3-102">IMetaDataEmit::DefineTypeDef – metoda</span><span class="sxs-lookup"><span data-stu-id="bcfc3-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="bcfc3-103">Vytvoří definici typu pro typ modulu CLR (Common Language Runtime) a získá token metadat pro danou definici typu.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcfc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcfc3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcfc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bcfc3-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="bcfc3-106">pro Název typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="bcfc3-107">[in] `TypeDef` atributy.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="bcfc3-108">Toto je Bitová maska `CoreTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="bcfc3-109">pro Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-109">[in] The token of the base class.</span></span> <span data-ttu-id="bcfc3-110">Musí to být buď `mdTypeDef`, nebo token `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="bcfc3-111">pro Pole tokenů určující rozhraní, které tato třída nebo rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="bcfc3-112">mimo Byl přiřazen token `mdTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bcfc3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcfc3-113">Remarks</span></span>  
 <span data-ttu-id="bcfc3-114">Příznak v `dwTypeDefFlags` určuje, zda typ, který je vytvářen, je typ odkazu na běžný typ systému (třída nebo rozhraní) nebo běžný typ hodnoty systému.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="bcfc3-115">V závislosti na zadaných parametrech může tato metoda jako vedlejší efekt vytvořit také záznam `mdInterfaceImpl` pro každé rozhraní, které je zděděno nebo implementováno tímto typem.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="bcfc3-116">Tato metoda však nevrací žádné z těchto tokenů `mdInterfaceImpl`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="bcfc3-117">Pokud chce klient později přidat nebo změnit `mdInterfaceImpl` tokenu, musí k zobrazení výčtu použít rozhraní `IMetaDataImport`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="bcfc3-118">Pokud chcete použít sémantiku COM `[default]` rozhraní, měli byste zadat výchozí rozhraní jako první prvek v `rtkImplements`; vlastní atribut nastavený u třídy bude označovat, že třída má výchozí rozhraní (což se vždy předpokládá, že se jedná o první `mdInterfaceImpl` token deklarovaný pro třídu).</span><span class="sxs-lookup"><span data-stu-id="bcfc3-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="bcfc3-119">Každý prvek `rtkImplements` pole obsahuje token `mdTypeDef` nebo `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="bcfc3-120">Poslední prvek v poli musí být `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcfc3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bcfc3-121">Requirements</span></span>  
 <span data-ttu-id="bcfc3-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcfc3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcfc3-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bcfc3-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bcfc3-124">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bcfc3-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcfc3-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcfc3-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfc3-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcfc3-126">See also</span></span>

- [<span data-ttu-id="bcfc3-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcfc3-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bcfc3-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bcfc3-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
