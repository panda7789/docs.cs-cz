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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f74952c2b3960dc29e0d1970276d972b048837f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499157"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="dc651-102">IMetaDataImport::ResolveTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="dc651-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="dc651-103">Řeší <xref:System.Type> odkaz reprezentována zadaný token TypeRef.</span><span class="sxs-lookup"><span data-stu-id="dc651-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc651-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc651-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc651-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc651-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="dc651-106">[in] Token TypeRef metadat nevrátil informace odkazovaného typu pro.</span><span class="sxs-lookup"><span data-stu-id="dc651-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="dc651-107">[in] Identifikátor IID rozhraní vrátit v `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="dc651-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="dc651-108">Obvykle by to IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="dc651-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="dc651-109">[out] Rozhraní pro rozsah modulu, ve kterém odkazovaný typ je definován.</span><span class="sxs-lookup"><span data-stu-id="dc651-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="dc651-110">[out] Ukazatel na token TypeDef, který představuje odkazovaného typu.</span><span class="sxs-lookup"><span data-stu-id="dc651-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc651-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc651-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc651-112">Nepoužívejte tuto metodu, pokud jsou načteny více domén aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc651-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="dc651-113">Metoda nerespektuje hranice aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="dc651-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="dc651-114">Pokud jsou načteno více verzí sestavení a obsahují stejný typ s stejný obor názvů, metoda vrátí rozsah modulu první typu, které nalezne.</span><span class="sxs-lookup"><span data-stu-id="dc651-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="dc651-115">`ResolveTypeRef` Metoda vyhledá do definice typu v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="dc651-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="dc651-116">Pokud se najde definici typu `ResolveTypeRef` vrátí rozsah tohoto modulu, jakož i token TypeDef pro typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dc651-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="dc651-117">Pokud má rozlišení oboru odkaz AssemblyRef, které je potřeba vyřešit odkaz na typ `ResolveTypeRef` metoda vyhledá shodu pouze v obory metadat, které již byly otevřeny pomocí volání na buď [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metoda nebo [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="dc651-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="dc651-118">Důvodem je, že `ResolveTypeRef` nelze určit ze pouze odkaz AssemblyRef obor na disk nebo do globální mezipaměti sestavení sestavení se mají ukládat.</span><span class="sxs-lookup"><span data-stu-id="dc651-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc651-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc651-119">Requirements</span></span>  
 <span data-ttu-id="dc651-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc651-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc651-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc651-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc651-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc651-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc651-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc651-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc651-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc651-124">See also</span></span>
- [<span data-ttu-id="dc651-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc651-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dc651-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc651-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
