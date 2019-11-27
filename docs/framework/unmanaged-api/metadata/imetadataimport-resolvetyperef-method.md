---
title: IMetaDataImport::ResolveTypeRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 800b15bb75e74898cee9d838900ea14b60620940
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431468"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="9a990-102">IMetaDataImport::ResolveTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="9a990-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="9a990-103">Vyřeší odkaz na <xref:System.Type> reprezentovaný zadaným tokenem TypeRef.</span><span class="sxs-lookup"><span data-stu-id="9a990-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a990-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a990-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a990-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a990-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="9a990-106">pro Token metadat TypeRef, pro který se mají vrátit odkazované informace o typu pro.</span><span class="sxs-lookup"><span data-stu-id="9a990-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="9a990-107">pro IID rozhraní, které se má vrátit v `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="9a990-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="9a990-108">Obvykle by to bylo IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="9a990-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="9a990-109">mimo Rozhraní pro obor modulu, ve kterém je definován odkazovaný typ.</span><span class="sxs-lookup"><span data-stu-id="9a990-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="9a990-110">mimo Ukazatel na token TypeDef, který představuje odkazovaný typ.</span><span class="sxs-lookup"><span data-stu-id="9a990-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a990-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a990-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9a990-112">Tuto metodu nepoužívejte, pokud je načteno více domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a990-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="9a990-113">Metoda nerespektuje hranice aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="9a990-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="9a990-114">Je-li načteno více verzí sestavení a obsahují stejný typ se stejným oborem názvů, metoda vrátí rozsah modulu prvního hledaného typu.</span><span class="sxs-lookup"><span data-stu-id="9a990-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="9a990-115">Metoda `ResolveTypeRef` vyhledá definici typu v jiných modulech.</span><span class="sxs-lookup"><span data-stu-id="9a990-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="9a990-116">Pokud je nalezena definice typu, `ResolveTypeRef` vrátí rozhraní do tohoto oboru modulu a také token TypeDef pro typ.</span><span class="sxs-lookup"><span data-stu-id="9a990-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="9a990-117">Pokud odkaz na typ, který má být vyřešen, má obor rozlišení AssemblyRef, metoda `ResolveTypeRef` vyhledá shodu pouze v oborech metadat, které již byly otevřeny pomocí volání metody [IMetaDataDispenser:: OpenScope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) nebo metody [IMetaDataDispenser:: OpenScopeOnMemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9a990-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="9a990-118">Důvodem je, že `ResolveTypeRef` nelze určit pouze z oboru AssemblyRef, kde na disku nebo v globální mezipaměti sestavení (GAC) je sestavení uloženo.</span><span class="sxs-lookup"><span data-stu-id="9a990-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a990-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a990-119">Requirements</span></span>  
 <span data-ttu-id="9a990-120">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a990-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a990-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9a990-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a990-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9a990-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a990-123">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a990-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a990-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a990-124">See also</span></span>

- [<span data-ttu-id="9a990-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a990-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a990-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a990-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
