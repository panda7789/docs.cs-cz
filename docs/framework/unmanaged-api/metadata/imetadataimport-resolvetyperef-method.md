---
title: "IMetaDataImport::ResolveTypeRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResolveTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 390387abef5c48b4842adcfbfca126bb8292cc28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="00d2f-102">IMetaDataImport::ResolveTypeRef – metoda</span><span class="sxs-lookup"><span data-stu-id="00d2f-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="00d2f-103">Přeloží <xref:System.Type> odkaz reprezentována zadaný odkaz TypeRef token.</span><span class="sxs-lookup"><span data-stu-id="00d2f-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00d2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00d2f-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00d2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00d2f-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="00d2f-106">[v] Token metadata Odkaz TypeRef k vrácení informací odkazovaného typu pro.</span><span class="sxs-lookup"><span data-stu-id="00d2f-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="00d2f-107">[v] Identifikátory IID rozhraní se vrátit v `ppIScope`.</span><span class="sxs-lookup"><span data-stu-id="00d2f-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="00d2f-108">Obvykle to může být IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="00d2f-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="00d2f-109">[out] Rozhraní modulu oboru, ve kterém je definovaný odkazovaného typu.</span><span class="sxs-lookup"><span data-stu-id="00d2f-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="00d2f-110">[out] Ukazatel na TypeDef token, který představuje odkazovaného typu.</span><span class="sxs-lookup"><span data-stu-id="00d2f-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00d2f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="00d2f-111">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00d2f-112">Tato metoda nepoužívejte, pokud se načtou více domén aplikací.</span><span class="sxs-lookup"><span data-stu-id="00d2f-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="00d2f-113">Metoda nedodržuje hranice domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="00d2f-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="00d2f-114">Pokud se načtou více verzí sestavení a obsahují stejného typu se o stejný obor názvů, vrátí metoda rozsah modulu první typu, které najde.</span><span class="sxs-lookup"><span data-stu-id="00d2f-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="00d2f-115">`ResolveTypeRef` Metoda vyhledá definici typu v dalších modulů.</span><span class="sxs-lookup"><span data-stu-id="00d2f-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="00d2f-116">Pokud se najde definici typu `ResolveTypeRef` vrátí do oboru tohoto modulu a také token TypeDef pro typ rozhraní.</span><span class="sxs-lookup"><span data-stu-id="00d2f-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="00d2f-117">Pokud má odkaz na typ na možné přeložit na odkaz AssemblyRef, rozsah řešení `ResolveTypeRef` metoda vyhledá shodu pouze v obory metadat, která již byla otevřena pomocí volání buď [imetadatadispenser::openscope –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)metoda nebo [imetadatadispenser::openscopeonmemory –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="00d2f-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="00d2f-118">Důvodem je, že `ResolveTypeRef` nemůže zjistit z pouze odkaz AssemblyRef oboru na disk nebo do globální mezipaměti sestavení sestavení se uloží.</span><span class="sxs-lookup"><span data-stu-id="00d2f-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00d2f-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00d2f-119">Requirements</span></span>  
 <span data-ttu-id="00d2f-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00d2f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00d2f-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00d2f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00d2f-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00d2f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00d2f-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00d2f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d2f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d2f-124">See Also</span></span>  
 [<span data-ttu-id="00d2f-125">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00d2f-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="00d2f-126">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00d2f-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
