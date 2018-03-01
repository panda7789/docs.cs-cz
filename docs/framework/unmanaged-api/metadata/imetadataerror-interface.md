---
title: "IMetaDataError – rozhraní"
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
- IMetaDataError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError
helpviewer_keywords:
- IMetaDataError interface [.NET Framework metadata]
ms.assetid: 0020b62c-ea88-40c7-a9ee-16b064f81624
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4df7aa7400a180151de5420effc8738955d51c26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="82cb7-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82cb7-102">IMetaDataError Interface</span></span>
<span data-ttu-id="82cb7-103">Poskytuje mechanismus zpětného volání pro oznamování chyb během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="82cb7-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82cb7-104">`IMetaDataError` Rozhraní musí být implementována klientem.</span><span class="sxs-lookup"><span data-stu-id="82cb7-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82cb7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="82cb7-105">Methods</span></span>  
  
|<span data-ttu-id="82cb7-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="82cb7-106">Method</span></span>|<span data-ttu-id="82cb7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="82cb7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82cb7-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="82cb7-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="82cb7-109">Poskytuje oznámení chyb, ke kterým došlo během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="82cb7-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82cb7-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82cb7-110">Requirements</span></span>  
 <span data-ttu-id="82cb7-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82cb7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82cb7-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82cb7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82cb7-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82cb7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82cb7-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82cb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82cb7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="82cb7-115">See Also</span></span>  
 [<span data-ttu-id="82cb7-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="82cb7-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
