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
ms.openlocfilehash: 46370da4e61dc90f2386170745da4f95ac7de63b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492756"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="124eb-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="124eb-102">IMetaDataError Interface</span></span>
<span data-ttu-id="124eb-103">Poskytuje mechanismus zpětného volání pro hlášení chyb během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="124eb-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="124eb-104">`IMetaDataError`Rozhraní musí být implementováno klientem.</span><span class="sxs-lookup"><span data-stu-id="124eb-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="124eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="124eb-105">Methods</span></span>  
  
|<span data-ttu-id="124eb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="124eb-106">Method</span></span>|<span data-ttu-id="124eb-107">Description</span><span class="sxs-lookup"><span data-stu-id="124eb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="124eb-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="124eb-108">OnError Method</span></span>](imetadataerror-onerror-method.md)|<span data-ttu-id="124eb-109">Poskytuje oznámení o chybách, ke kterým došlo během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="124eb-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="124eb-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="124eb-110">Requirements</span></span>  
 <span data-ttu-id="124eb-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="124eb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="124eb-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="124eb-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="124eb-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="124eb-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="124eb-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="124eb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="124eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="124eb-115">See also</span></span>

- [<span data-ttu-id="124eb-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="124eb-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
