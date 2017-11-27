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
ms.openlocfilehash: a872af384a8df624178d8d37d5ad98a0b5c561d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="f2fb1-102">IMetaDataImport::EnumTypeSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="f2fb1-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="f2fb1-103">Zobrazí typ TypeSpec tokeny definované v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2fb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2fb1-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2fb1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2fb1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f2fb1-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f2fb1-107">Tato hodnota musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="f2fb1-108">[out] Pole používá k ukládání typ TypeSpec tokenů.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f2fb1-109">[v] Maximální velikost `rTypeSpecs` pole.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="f2fb1-110">[out] Počet typ TypeSpec tokeny, vrátí se v `rTypeSpecs`.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2fb1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f2fb1-111">Return Value</span></span>  
  
|<span data-ttu-id="f2fb1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2fb1-112">HRESULT</span></span>|<span data-ttu-id="f2fb1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f2fb1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f2fb1-114">`EnumTypeSpecs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f2fb1-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="f2fb1-116">V takovém případě `pcTypeSpecs` je nulová.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2fb1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2fb1-117">Remarks</span></span>  
 <span data-ttu-id="f2fb1-118">Typ TypeSpec tokeny jsou vytvořené pomocí [imetadataemit::gettokenfromtypespec –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="f2fb1-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2fb1-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2fb1-119">Requirements</span></span>  
 <span data-ttu-id="f2fb1-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2fb1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2fb1-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2fb1-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2fb1-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f2fb1-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2fb1-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2fb1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2fb1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2fb1-124">See Also</span></span>  
 [<span data-ttu-id="f2fb1-125">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2fb1-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f2fb1-126">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f2fb1-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
