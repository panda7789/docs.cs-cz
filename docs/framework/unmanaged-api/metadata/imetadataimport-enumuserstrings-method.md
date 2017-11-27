---
title: "IMetaDataImport::EnumUserStrings – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUserStrings
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 48ec44d993c5cdc2c545125bf8b4bcb80e413f95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="6f8c9-102">IMetaDataImport::EnumUserStrings – metoda</span><span class="sxs-lookup"><span data-stu-id="6f8c9-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="6f8c9-103">Vytvoří výčet tokeny řetězec představující pevně řetězce v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f8c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f8c9-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f8c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f8c9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6f8c9-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6f8c9-107">Toto musí mít hodnotu NULL pro první volání této metody.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="6f8c9-108">[out] Pole používá k ukládání tokeny řetězec.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6f8c9-109">[v] Maximální velikost `rStrings` pole.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="6f8c9-110">[out] Počet řetězec tokeny, vrátí se v `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f8c9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6f8c9-111">Return Value</span></span>  
  
|<span data-ttu-id="6f8c9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f8c9-112">HRESULT</span></span>|<span data-ttu-id="6f8c9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6f8c9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6f8c9-114">`EnumUserStrings`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6f8c9-115">Neexistují žádné tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6f8c9-116">V takovém případě `pcStrings` je nulová.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f8c9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f8c9-117">Remarks</span></span>  
 <span data-ttu-id="6f8c9-118">Řetězec tokeny jsou vytvořené pomocí [imetadataemit::defineuserstring –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="6f8c9-119">Tato metoda je určena pro použití prohlížečem metadata, a nikoli kompilátor.</span><span class="sxs-lookup"><span data-stu-id="6f8c9-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f8c9-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f8c9-120">Requirements</span></span>  
 <span data-ttu-id="6f8c9-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f8c9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f8c9-122">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f8c9-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f8c9-123">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f8c9-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f8c9-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f8c9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f8c9-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f8c9-125">See Also</span></span>  
 [<span data-ttu-id="6f8c9-126">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f8c9-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="6f8c9-127">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6f8c9-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
