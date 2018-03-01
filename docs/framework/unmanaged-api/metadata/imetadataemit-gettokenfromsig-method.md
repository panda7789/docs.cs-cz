---
title: "IMetaDataEmit::GetTokenFromSig – metoda"
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
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: df454b8dd95839f4cabe3c725e206f3683437ec4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="510a9-102">IMetaDataEmit::GetTokenFromSig – metoda</span><span class="sxs-lookup"><span data-stu-id="510a9-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="510a9-103">Získá token pro podpis Zadaná metadata.</span><span class="sxs-lookup"><span data-stu-id="510a9-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="510a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="510a9-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="510a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="510a9-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="510a9-106">[v] Podpis trvalé a uložené.</span><span class="sxs-lookup"><span data-stu-id="510a9-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="510a9-107">[v] Počet bajtů v `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="510a9-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="510a9-108">[out] `mdSignature` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="510a9-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="510a9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="510a9-109">Requirements</span></span>  
 <span data-ttu-id="510a9-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="510a9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="510a9-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="510a9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="510a9-112">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="510a9-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="510a9-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="510a9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="510a9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="510a9-114">See Also</span></span>  
 [<span data-ttu-id="510a9-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="510a9-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="510a9-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="510a9-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
