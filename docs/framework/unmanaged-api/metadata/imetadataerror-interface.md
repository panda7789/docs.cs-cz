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
ms.openlocfilehash: 44ecb73375f8a408fb0a38c3a2e2913f92ec4ca4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441629"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="45831-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="45831-102">IMetaDataError Interface</span></span>
<span data-ttu-id="45831-103">Poskytuje mechanismus zpětného volání pro hlášení chyb během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="45831-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45831-104">Rozhraní `IMetaDataError` musí být implementováno klientem.</span><span class="sxs-lookup"><span data-stu-id="45831-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45831-105">Metody</span><span class="sxs-lookup"><span data-stu-id="45831-105">Methods</span></span>  
  
|<span data-ttu-id="45831-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="45831-106">Method</span></span>|<span data-ttu-id="45831-107">Popis</span><span class="sxs-lookup"><span data-stu-id="45831-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45831-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="45831-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="45831-109">Poskytuje oznámení o chybách, ke kterým došlo během sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="45831-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45831-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45831-110">Requirements</span></span>  
 <span data-ttu-id="45831-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45831-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45831-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="45831-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45831-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="45831-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45831-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45831-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45831-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45831-115">See also</span></span>

- [<span data-ttu-id="45831-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="45831-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
