---
title: IApartmentCallback – rozhraní
ms.date: 03/30/2017
api_name:
- IApartmentCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IApartmentCallback
helpviewer_keywords:
- IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db933716cc0602ecda5da8a72726408ae4910179
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129802"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="366a6-102">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="366a6-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="366a6-103">Poskytuje metody pro provádění zpětných volání v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="366a6-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="366a6-104">*Objektu apartment* je logický kontejner, v rámci procesu pro objekty, které sdílejí stejné požadavky na přístup vlákna.</span><span class="sxs-lookup"><span data-stu-id="366a6-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="366a6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="366a6-105">Methods</span></span>  
  
|<span data-ttu-id="366a6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="366a6-106">Method</span></span>|<span data-ttu-id="366a6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="366a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="366a6-108">DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="366a6-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="366a6-109">Provede zadanou funkci v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="366a6-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="366a6-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="366a6-110">Requirements</span></span>  
 <span data-ttu-id="366a6-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="366a6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="366a6-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="366a6-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="366a6-113">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="366a6-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="366a6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="366a6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="366a6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="366a6-115">See also</span></span>

- [<span data-ttu-id="366a6-116">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="366a6-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
