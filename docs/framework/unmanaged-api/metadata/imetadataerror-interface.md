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
ms.openlocfilehash: 37f1f6055ec8fa68fe804780d2893d20c978e6bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663750"
---
# <a name="imetadataerror-interface"></a><span data-ttu-id="d4c45-102">IMetaDataError – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4c45-102">IMetaDataError Interface</span></span>
<span data-ttu-id="d4c45-103">Poskytuje mechanismus zpětného volání pro zasílání zpráv o chybách během metadat sloučení.</span><span class="sxs-lookup"><span data-stu-id="d4c45-103">Provides a callback mechanism for reporting errors during the metadata merge.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4c45-104">`IMetaDataError` Pomocí klienta musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d4c45-104">The `IMetaDataError` interface must be implemented by the client.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4c45-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d4c45-105">Methods</span></span>  
  
|<span data-ttu-id="d4c45-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="d4c45-106">Method</span></span>|<span data-ttu-id="d4c45-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d4c45-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4c45-108">OnError – metoda</span><span class="sxs-lookup"><span data-stu-id="d4c45-108">OnError Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-onerror-method.md)|<span data-ttu-id="d4c45-109">Poskytuje oznámení chyb, k nimž došlo při sloučení metadat.</span><span class="sxs-lookup"><span data-stu-id="d4c45-109">Provides notification of errors that occur during the metadata merge.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d4c45-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4c45-110">Requirements</span></span>  
 <span data-ttu-id="d4c45-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4c45-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4c45-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d4c45-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4c45-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4c45-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4c45-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4c45-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c45-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d4c45-115">See also</span></span>

- [<span data-ttu-id="d4c45-116">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="d4c45-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
