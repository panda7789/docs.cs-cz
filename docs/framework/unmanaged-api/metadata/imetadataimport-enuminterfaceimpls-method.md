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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21d70b2702a754b554f06de5dad776ae98ae918d
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836263"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="ad56a-102">IMetaDataImport::EnumInterfaceImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="ad56a-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="ad56a-103">Vytvoří výčet všech rozhraní implementované zadanou `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="ad56a-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="ad56a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad56a-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad56a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad56a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ad56a-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ad56a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ad56a-107">[in] Token TypeDef, jehož MethodDef tokeny představující implementace rozhraní jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="ad56a-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="ad56a-108">[out] Pole pro ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="ad56a-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ad56a-109">[in] Maximální velikost `rImpls` pole.</span><span class="sxs-lookup"><span data-stu-id="ad56a-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="ad56a-110">[out] Skutečný počet tokenů vrátil v `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="ad56a-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad56a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ad56a-111">Return Value</span></span>  
  
|<span data-ttu-id="ad56a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad56a-112">HRESULT</span></span>|<span data-ttu-id="ad56a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ad56a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ad56a-114">`EnumInterfaceImpls` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ad56a-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ad56a-115">Neexistují žádné tokeny MethodDef k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="ad56a-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="ad56a-116">V takovém případě `pcImpls` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="ad56a-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="ad56a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad56a-117">Remarks</span></span>

<span data-ttu-id="ad56a-118">Vrátí kolekci výčtu `mdInterfaceImpl` tokeny pro každé rozhraní implementované zadanou `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="ad56a-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="ad56a-119">Rozhraní tokeny jsou vráceny v pořadí, které byly zadány rozhraní (prostřednictvím `DefineTypeDef` nebo `SetTypeDefProps`).</span><span class="sxs-lookup"><span data-stu-id="ad56a-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="ad56a-120">Vlastnosti vráceného `mdInterfaceImpl` tokeny, může být dotázán pomocí [getinterfaceimplprops –](imetadataimport-getinterfaceimplprops-method.md).</span><span class="sxs-lookup"><span data-stu-id="ad56a-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ad56a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad56a-121">Requirements</span></span>  
 <span data-ttu-id="ad56a-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad56a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad56a-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad56a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad56a-124">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad56a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad56a-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad56a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad56a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad56a-126">See also</span></span>
- [<span data-ttu-id="ad56a-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad56a-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ad56a-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad56a-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
