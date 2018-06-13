---
title: IMetaDataError – rozhraní
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1c264bfd31f8cd31bacf2d194ddbd07338569294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447167"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="9089a-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9089a-102">IMetaDataError Interface</span></span>
<span data-ttu-id="9089a-103">Poskytuje mechanismus zpětného volání pro oznamování chyb během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="9089a-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9089a-104">`IMetaDataError` Rozhraní musí být implementována klientem.</span><span class="sxs-lookup"><span data-stu-id="9089a-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9089a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9089a-105">Methods</span></span>  
  
|<span data-ttu-id="9089a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9089a-106">Method</span></span>|<span data-ttu-id="9089a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9089a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9089a-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="9089a-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="9089a-109">Poskytuje oznámení chyb, ke kterým došlo během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="9089a-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9089a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9089a-110">Requirements</span></span>  
 <span data-ttu-id="9089a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9089a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9089a-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9089a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9089a-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9089a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9089a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9089a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9089a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9089a-115">See Also</span></span>  
 [<span data-ttu-id="9089a-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="9089a-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
