---
title: "IMetaDataEmit::GetTokenFromTypeSpec – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromTypeSpec
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f83d1adb37691b525927eeb8a87b620fa3c7353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="64503-102">IMetaDataEmit::GetTokenFromTypeSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="64503-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="64503-103">Získá token metadat pro typ s podpisem Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="64503-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64503-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64503-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64503-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64503-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="64503-106">[v] Podpis definovaný.</span><span class="sxs-lookup"><span data-stu-id="64503-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="64503-107">[v] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="64503-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="64503-108">[out] `mdTypeSpec` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="64503-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64503-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="64503-109">Requirements</span></span>  
 <span data-ttu-id="64503-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64503-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64503-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="64503-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64503-112">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64503-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64503-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64503-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64503-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="64503-114">See Also</span></span>  
 [<span data-ttu-id="64503-115">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64503-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="64503-116">Imetadataemit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="64503-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
