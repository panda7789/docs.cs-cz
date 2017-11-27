---
title: "IMetaDataImport::GetSigFromToken – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetSigFromToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab7df32641d4fcd093f1ed31eb9ed7c7954e6bf8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="14800-102">IMetaDataImport::GetSigFromToken – metoda</span><span class="sxs-lookup"><span data-stu-id="14800-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="14800-103">Získá podpis binární metadata související s zadaný token.</span><span class="sxs-lookup"><span data-stu-id="14800-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14800-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14800-104">Syntax</span></span>  
  
```  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14800-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14800-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="14800-106">[v] Token, který se má vrátit binární metadata podpis pro.</span><span class="sxs-lookup"><span data-stu-id="14800-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="14800-107">[out] Ukazatel na podpis Vrácená metadata.</span><span class="sxs-lookup"><span data-stu-id="14800-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="14800-108">[out] Velikost v bajtech podpisu binární metadat.</span><span class="sxs-lookup"><span data-stu-id="14800-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14800-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14800-109">Requirements</span></span>  
 <span data-ttu-id="14800-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14800-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14800-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14800-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14800-112">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14800-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14800-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14800-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14800-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="14800-114">See Also</span></span>  
 [<span data-ttu-id="14800-115">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14800-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="14800-116">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14800-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
