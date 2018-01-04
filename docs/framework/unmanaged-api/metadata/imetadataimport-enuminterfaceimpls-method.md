---
title: "IMetaDataImport::EnumInterfaceImpls – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumInterfaceImpls
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 646d65ff81795ce0558651db9c3fe1bc7205ae08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="ecc64-102">IMetaDataImport::EnumInterfaceImpls – metoda</span><span class="sxs-lookup"><span data-stu-id="ecc64-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="ecc64-103">Vytvoří výčet MethodDef tokeny představující implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ecc64-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc64-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecc64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecc64-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ecc64-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="ecc64-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ecc64-107">[v] Token TypeDef, jejichž MethodDef tokeny představující implementace rozhraní jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="ecc64-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="ecc64-108">[out] Pole používá k ukládání MethodDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="ecc64-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ecc64-109">[v] Maximální velikost `rImpls` pole.</span><span class="sxs-lookup"><span data-stu-id="ecc64-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="ecc64-110">[out] Skutečný počet tokeny, vrátí se v `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="ecc64-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecc64-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ecc64-111">Return Value</span></span>  
  
|<span data-ttu-id="ecc64-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecc64-112">HRESULT</span></span>|<span data-ttu-id="ecc64-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc64-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ecc64-114">`EnumInterfaceImpls`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="ecc64-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ecc64-115">Neexistují žádné MethodDef tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="ecc64-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="ecc64-116">V takovém případě `pcImpls` je nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="ecc64-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecc64-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecc64-117">Requirements</span></span>  
 <span data-ttu-id="ecc64-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc64-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc64-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ecc64-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ecc64-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ecc64-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc64-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc64-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc64-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc64-122">See Also</span></span>  
 [<span data-ttu-id="ecc64-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc64-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="ecc64-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ecc64-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
