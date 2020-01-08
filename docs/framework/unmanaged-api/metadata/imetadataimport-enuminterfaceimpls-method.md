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
ms.openlocfilehash: ef7057ad19fd34750bd15d358e9c1ebb1289cd44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338054"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="b966e-102">IMetaDataImport::EnumInterfaceImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="b966e-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="b966e-103">Vytvoří výčet všech rozhraní implementovaných specifikovaným `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="b966e-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="b966e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b966e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b966e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b966e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b966e-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b966e-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="b966e-107">pro Token TypeDef, jehož tokeny MethodDef představují implementaci rozhraní, mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="b966e-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="b966e-108">mimo Pole použité k uložení tokenů MethodDef</span><span class="sxs-lookup"><span data-stu-id="b966e-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b966e-109">pro Maximální délka `rImpls` pole.</span><span class="sxs-lookup"><span data-stu-id="b966e-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="b966e-110">mimo Skutečný počet tokenů vrácených v `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="b966e-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b966e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b966e-111">Return Value</span></span>  
  
|<span data-ttu-id="b966e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b966e-112">HRESULT</span></span>|<span data-ttu-id="b966e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b966e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b966e-114">`EnumInterfaceImpls` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b966e-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b966e-115">Nejsou k dispozici žádné tokeny MethodDef pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="b966e-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="b966e-116">V takovém případě je `pcImpls` nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="b966e-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="b966e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b966e-117">Remarks</span></span>

<span data-ttu-id="b966e-118">Výčet vrátí kolekci `mdInterfaceImpl`ch tokenů pro každé rozhraní implementované určeného `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="b966e-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="b966e-119">Tokeny rozhraní jsou vraceny v pořadí, ve kterém byla rozhraní zadána (prostřednictvím `DefineTypeDef` nebo `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="b966e-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="b966e-120">K vlastnostem vrácených tokenů `mdInterfaceImpl` se dá dotázat pomocí [getinterfaceimplprops –](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="b966e-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="b966e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b966e-121">Requirements</span></span>  
 <span data-ttu-id="b966e-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b966e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b966e-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b966e-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b966e-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b966e-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b966e-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b966e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b966e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b966e-126">See also</span></span>

- [<span data-ttu-id="b966e-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b966e-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b966e-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b966e-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
