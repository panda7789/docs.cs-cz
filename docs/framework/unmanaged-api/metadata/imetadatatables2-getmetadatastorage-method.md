---
title: "IMetaDataTables2::GetMetaDataStorage – metoda"
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
- IMetaDataTables2.GetMetaDataStorage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b00d03f8bd4a355d309f1a1266ca68f73647e0dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="5c828-102">IMetaDataTables2::GetMetaDataStorage – metoda</span><span class="sxs-lookup"><span data-stu-id="5c828-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="5c828-103">Získá velikost a obsah metadata uložená v zadaný oddíl.</span><span class="sxs-lookup"><span data-stu-id="5c828-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c828-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c828-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c828-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="5c828-106">[ve out] Ukazatel na část metadat.</span><span class="sxs-lookup"><span data-stu-id="5c828-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="5c828-107">[out] Velikost datového proudu metadat.</span><span class="sxs-lookup"><span data-stu-id="5c828-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c828-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c828-108">Requirements</span></span>  
 <span data-ttu-id="5c828-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c828-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c828-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c828-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c828-111">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c828-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c828-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c828-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c828-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c828-113">See Also</span></span>  
 [<span data-ttu-id="5c828-114">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c828-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="5c828-115">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c828-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
