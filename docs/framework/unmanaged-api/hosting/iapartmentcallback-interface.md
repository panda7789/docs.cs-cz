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
ms.openlocfilehash: ffa06fd42b5cfa09817bae9f0b3a3810e30f99c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430964"
---
# <a name="iapartmentcallback-interface"></a><span data-ttu-id="72c72-102">IApartmentCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72c72-102">IApartmentCallback Interface</span></span>
<span data-ttu-id="72c72-103">Poskytuje metody pro provádění zpětných volání v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="72c72-103">Provides methods for making callbacks within an apartment.</span></span> <span data-ttu-id="72c72-104">*Apartment* je logický kontejner v rámci procesu pro objekty, které sdílejí stejné požadavky na přístup přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="72c72-104">An *apartment* is a logical container within a process for objects that share the same thread access requirements.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72c72-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72c72-105">Methods</span></span>  
  
|<span data-ttu-id="72c72-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="72c72-106">Method</span></span>|<span data-ttu-id="72c72-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72c72-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72c72-108">DoCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="72c72-108">DoCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-docallback-method.md)|<span data-ttu-id="72c72-109">Provede zadanou funkci v rámci typu apartment.</span><span class="sxs-lookup"><span data-stu-id="72c72-109">Executes the specified function within an apartment.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72c72-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72c72-110">Requirements</span></span>  
 <span data-ttu-id="72c72-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72c72-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72c72-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72c72-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72c72-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72c72-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72c72-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72c72-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c72-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="72c72-115">See Also</span></span>  
 [<span data-ttu-id="72c72-116">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="72c72-116">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
