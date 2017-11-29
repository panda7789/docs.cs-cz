---
title: "IApartmentCallback – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IApartmentCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: IApartmentCallback
helpviewer_keywords: IApartmentCallback interface [.NET Framework hosting]
ms.assetid: 57c33c58-bf0b-4533-b569-e6a682d02cba
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d2f2ea73da2273ff6f0abb725ec3e3fb8ca79ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="4860f-102">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4860f-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="4860f-103">Poskytuje metody pro provádění zpětných volání v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="4860f-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="4860f-104">*Apartment* je logický kontejner v rámci procesu pro objekty, které sdílejí stejné požadavky na přístup přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="4860f-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4860f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4860f-105">Methods</span></span>  
  
|<span data-ttu-id="4860f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4860f-106">Method</span></span>|<span data-ttu-id="4860f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4860f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4860f-108">DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="4860f-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="4860f-109">Provede zadanou funkci v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="4860f-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4860f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4860f-110">Requirements</span></span>  
 <span data-ttu-id="4860f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4860f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4860f-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4860f-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4860f-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4860f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4860f-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4860f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4860f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4860f-115">See Also</span></span>  
 [<span data-ttu-id="4860f-116">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="4860f-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
