---
title: "IMetaDataTables::GetGuidHeapSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuidHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76a2aa4495a9f34a57c8a84ec40ab946abc64532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="ed4ff-102">IMetaDataTables::GetGuidHeapSize – metoda</span><span class="sxs-lookup"><span data-stu-id="ed4ff-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="ed4ff-103">Získá velikost v bajtech haldě identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="ed4ff-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed4ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed4ff-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed4ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed4ff-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="ed4ff-106">[out] Ukazatel na velikost v bajtech haldě identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="ed4ff-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed4ff-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed4ff-107">Requirements</span></span>  
 <span data-ttu-id="ed4ff-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed4ff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed4ff-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ed4ff-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ed4ff-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed4ff-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ed4ff-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed4ff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4ff-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed4ff-112">See Also</span></span>  
 [<span data-ttu-id="ed4ff-113">Imetadatatables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed4ff-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="ed4ff-114">Imetadatatables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed4ff-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
