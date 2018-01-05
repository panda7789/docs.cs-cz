---
title: "IMetaDataImport::EnumTypeSpecs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumTypeSpecs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e34a3086474918c913a366c02bbf9eadf313b43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="3062c-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="3062c-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="3062c-103">Zobrazí typ TypeSpec tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="3062c-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3062c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3062c-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3062c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3062c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3062c-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="3062c-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="3062c-107">Tato hodnota musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="3062c-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="3062c-108">[out] Pole používá k ukládání typ TypeSpec tokenů.</span><span class="sxs-lookup"><span data-stu-id="3062c-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3062c-109">[v] Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="3062c-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="3062c-110">[out] Počet typ TypeSpec tokeny, vrátí se v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="3062c-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3062c-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3062c-111">Return Value</span></span>  
  
|<span data-ttu-id="3062c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3062c-112">HRESULT</span></span>|<span data-ttu-id="3062c-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3062c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3062c-114">`EnumTypeSpecs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3062c-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3062c-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="3062c-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3062c-116">V takovém případě `pcTypeSpecs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="3062c-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3062c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3062c-117">Remarks</span></span>  
 <span data-ttu-id="3062c-118">Typ TypeSpec tokeny jsou vytvořené pomocí [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="3062c-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3062c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3062c-119">Requirements</span></span>  
 <span data-ttu-id="3062c-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3062c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3062c-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3062c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3062c-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3062c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3062c-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3062c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3062c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3062c-124">See Also</span></span>  
 [<span data-ttu-id="3062c-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3062c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="3062c-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3062c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
