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
ms.openlocfilehash: dc064b00e32bb6b1d8c2d0c20f571b35919eae23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009337"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="be707-102">IMetaDataEmit::DefineTypeDef – metoda</span><span class="sxs-lookup"><span data-stu-id="be707-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="be707-103">Vytvoří definici typu pro typ modulu CLR (Common Language Runtime) a získá token metadat pro danou definici typu.</span><span class="sxs-lookup"><span data-stu-id="be707-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be707-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be707-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be707-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be707-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="be707-106">pro Název typu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="be707-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="be707-107">[in] `TypeDef` atribut.</span><span class="sxs-lookup"><span data-stu-id="be707-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="be707-108">Toto je Bitová maska `CoreTypeAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="be707-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="be707-109">pro Token základní třídy.</span><span class="sxs-lookup"><span data-stu-id="be707-109">[in] The token of the base class.</span></span> <span data-ttu-id="be707-110">Musí to být buď `mdTypeDef` token, nebo `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="be707-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="be707-111">pro Pole tokenů určující rozhraní, které tato třída nebo rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="be707-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="be707-112">mimo `mdTypeDef`Přiřazený token.</span><span class="sxs-lookup"><span data-stu-id="be707-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be707-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be707-113">Remarks</span></span>  
 <span data-ttu-id="be707-114">Příznak v `dwTypeDefFlags` Určuje, zda typ, který je vytvářen, je typ odkazu na běžný typ systému (třída nebo rozhraní) nebo běžný typ hodnoty systému.</span><span class="sxs-lookup"><span data-stu-id="be707-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="be707-115">V závislosti na zadaných parametrech může tato metoda jako vedlejší efekt vytvořit také `mdInterfaceImpl` záznam pro každé rozhraní, které je zděděno nebo implementováno tímto typem.</span><span class="sxs-lookup"><span data-stu-id="be707-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="be707-116">Tato metoda však nevrátí žádnou z těchto `mdInterfaceImpl` tokenů.</span><span class="sxs-lookup"><span data-stu-id="be707-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="be707-117">Pokud chce klient později přidat nebo změnit `mdInterfaceImpl` token, musí `IMetaDataImport` k zobrazení výčtu použít rozhraní.</span><span class="sxs-lookup"><span data-stu-id="be707-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="be707-118">Pokud chcete použít sémantiku modelu COM `[default]` rozhraní, měli byste zadat výchozí rozhraní jako první prvek v `rtkImplements` ; vlastní atribut nastavený ve třídě bude označovat, že třída má výchozí rozhraní (což je vždy považováno za první `mdInterfaceImpl` token deklarovaný pro třídu).</span><span class="sxs-lookup"><span data-stu-id="be707-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="be707-119">Každý prvek `rtkImplements` pole obsahuje `mdTypeDef` `mdTypeRef` token nebo.</span><span class="sxs-lookup"><span data-stu-id="be707-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="be707-120">Poslední prvek v poli musí být `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="be707-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be707-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be707-121">Requirements</span></span>  
 <span data-ttu-id="be707-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be707-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be707-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="be707-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be707-124">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="be707-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be707-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be707-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be707-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="be707-126">See also</span></span>

- [<span data-ttu-id="be707-127">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be707-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="be707-128">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be707-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
