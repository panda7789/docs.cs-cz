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
ms.openlocfilehash: c94960478e6b2eb4e7b8f1e9592b0831af3ec686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603765"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="85de0-102">IMetaDataImport::EnumInterfaceImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="85de0-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="85de0-103">Vytvoří výčet MethodDef tokeny představující implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="85de0-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85de0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85de0-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85de0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85de0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="85de0-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="85de0-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="85de0-107">[in] Token TypeDef, jehož MethodDef tokeny představující implementace rozhraní jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="85de0-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="85de0-108">[out] Pole pro ukládání tokenů MethodDef.</span><span class="sxs-lookup"><span data-stu-id="85de0-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="85de0-109">[in] Maximální velikost `rImpls` pole.</span><span class="sxs-lookup"><span data-stu-id="85de0-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="85de0-110">[out] Skutečný počet tokenů vrátil v `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="85de0-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85de0-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="85de0-111">Return Value</span></span>  
  
|<span data-ttu-id="85de0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85de0-112">HRESULT</span></span>|<span data-ttu-id="85de0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="85de0-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="85de0-114">`EnumInterfaceImpls` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="85de0-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="85de0-115">Neexistují žádné tokeny MethodDef k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="85de0-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="85de0-116">V takovém případě `pcImpls` je nastavena na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="85de0-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85de0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85de0-117">Requirements</span></span>  
 <span data-ttu-id="85de0-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85de0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85de0-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85de0-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85de0-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85de0-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85de0-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85de0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85de0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85de0-122">See also</span></span>
- [<span data-ttu-id="85de0-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85de0-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="85de0-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85de0-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
