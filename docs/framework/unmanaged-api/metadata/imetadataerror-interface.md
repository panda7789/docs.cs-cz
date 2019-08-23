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
ms.openlocfilehash: 277b93267f0537c8e499a8d8f3b456c4396a975c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966343"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="8b791-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b791-102">IMetaDataError Interface</span></span>
<span data-ttu-id="8b791-103">Poskytuje mechanismus zpětného volání pro hlášení chyb během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="8b791-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b791-104">`IMetaDataError` Rozhraní musí být implementováno klientem.</span><span class="sxs-lookup"><span data-stu-id="8b791-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b791-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8b791-105">Methods</span></span>  
  
|<span data-ttu-id="8b791-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b791-106">Method</span></span>|<span data-ttu-id="8b791-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8b791-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b791-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="8b791-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="8b791-109">Poskytuje oznámení o chybách, ke kterým došlo během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="8b791-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b791-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b791-110">Requirements</span></span>  
 <span data-ttu-id="8b791-111">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b791-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b791-112">**Hlaviček** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b791-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b791-113">**Knihovna** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="8b791-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8b791-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b791-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b791-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b791-115">See also</span></span>

- [<span data-ttu-id="8b791-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="8b791-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
