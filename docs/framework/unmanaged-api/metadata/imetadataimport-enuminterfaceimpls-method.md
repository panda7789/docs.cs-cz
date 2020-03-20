---
title: IMetaDataImport::EnumInterfaceImpls – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175496"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="5db8b-102">IMetaDataImport::EnumInterfaceImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="5db8b-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="5db8b-103">Vyjmenovává všechna rozhraní implementovaná zadaným `TypeDef`rozhraním .</span><span class="sxs-lookup"><span data-stu-id="5db8b-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="5db8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5db8b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5db8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5db8b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5db8b-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="5db8b-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="5db8b-107">[v] Token TypeDef, jehož Tokeny MethodDef představující implementace rozhraní mají být uvedeny ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="5db8b-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="5db8b-108">[out] Pole používané k ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="5db8b-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5db8b-109">[v] Maximální délka `rImpls` pole.</span><span class="sxs-lookup"><span data-stu-id="5db8b-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="5db8b-110">[out] Skutečný počet tokenů vrácených v `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="5db8b-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5db8b-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5db8b-111">Return Value</span></span>  
  
|<span data-ttu-id="5db8b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5db8b-112">HRESULT</span></span>|<span data-ttu-id="5db8b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5db8b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5db8b-114">`EnumInterfaceImpls`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="5db8b-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5db8b-115">Neexistují žádné tokeny MethodDef k výčetu.</span><span class="sxs-lookup"><span data-stu-id="5db8b-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="5db8b-116">V takovém `pcImpls` případě je nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="5db8b-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="5db8b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5db8b-117">Remarks</span></span>

<span data-ttu-id="5db8b-118">Výčet vrátí kolekci `mdInterfaceImpl` tokenů pro každé rozhraní `TypeDef`implementované zadaným .</span><span class="sxs-lookup"><span data-stu-id="5db8b-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="5db8b-119">Tokeny rozhraní jsou vráceny v pořadí, `DefineTypeDef` v `SetTypeDefProps`jakém byla rozhraní zadána (prostřednictvím nebo ).</span><span class="sxs-lookup"><span data-stu-id="5db8b-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="5db8b-120">Vlastnosti vrácených `mdInterfaceImpl` tokenů lze dotazovat pomocí [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="5db8b-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="5db8b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5db8b-121">Requirements</span></span>  
 <span data-ttu-id="5db8b-122">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5db8b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5db8b-123">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="5db8b-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5db8b-124">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5db8b-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5db8b-125">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5db8b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db8b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5db8b-126">See also</span></span>

- [<span data-ttu-id="5db8b-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5db8b-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5db8b-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5db8b-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
