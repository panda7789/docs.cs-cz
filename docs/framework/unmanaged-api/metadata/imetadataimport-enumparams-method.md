---
title: "IMetaDataImport::EnumParams – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 51544a44ed4bae25d4214e25c717769a8446f0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="6a58f-102">IMetaDataImport::EnumParams – metoda</span><span class="sxs-lookup"><span data-stu-id="6a58f-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="6a58f-103">Vytvoří výčet představující parametry metody odkazuje zadaný token MethodDef tokeny ParamDef.</span><span class="sxs-lookup"><span data-stu-id="6a58f-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a58f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a58f-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a58f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a58f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6a58f-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6a58f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6a58f-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="6a58f-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="6a58f-108">[v] MethodDef token představující metodu s parametry, které chcete vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="6a58f-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="6a58f-109">[out] Pole používá k ukládání ParamDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="6a58f-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6a58f-110">[v] Maximální velikost `rParams` pole.</span><span class="sxs-lookup"><span data-stu-id="6a58f-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6a58f-111">[out] Počet ParamDef tokeny, vrátí se v `rParams`.</span><span class="sxs-lookup"><span data-stu-id="6a58f-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a58f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6a58f-112">Return Value</span></span>  
  
|<span data-ttu-id="6a58f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6a58f-113">HRESULT</span></span>|<span data-ttu-id="6a58f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6a58f-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6a58f-115">`EnumParams`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6a58f-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6a58f-116">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="6a58f-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="6a58f-117">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="6a58f-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a58f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6a58f-118">Requirements</span></span>  
 <span data-ttu-id="6a58f-119">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a58f-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a58f-120">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a58f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a58f-121">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6a58f-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a58f-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a58f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a58f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a58f-123">See Also</span></span>  
 [<span data-ttu-id="6a58f-124">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a58f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6a58f-125">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6a58f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
