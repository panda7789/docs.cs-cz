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
ms.openlocfilehash: fe2f683ae46d1ee6205f97536976a358e86fc53d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720376"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="b0a38-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0a38-102">IMetaDataError Interface</span></span>
<span data-ttu-id="b0a38-103">Poskytuje mechanismus zpětného volání pro zasílání zpráv o chybách během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="b0a38-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0a38-104">`IMetaDataError` Pomocí klienta musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b0a38-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0a38-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0a38-105">Methods</span></span>  
  
|<span data-ttu-id="b0a38-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0a38-106">Method</span></span>|<span data-ttu-id="b0a38-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b0a38-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0a38-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="b0a38-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="b0a38-109">Poskytuje oznámení chyb, k nimž došlo při sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="b0a38-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0a38-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0a38-110">Requirements</span></span>  
 <span data-ttu-id="b0a38-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0a38-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0a38-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0a38-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0a38-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0a38-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0a38-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0a38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0a38-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0a38-115">See also</span></span>
- [<span data-ttu-id="b0a38-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="b0a38-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
