---
title: IHostControl – rozhraní
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 444a78705c61d5a53764f55185ef1a907830bd71
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195883"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="a701e-102">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a701e-102">IHostControl Interface</span></span>
<span data-ttu-id="a701e-103">Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="a701e-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a701e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a701e-104">Methods</span></span>  
  
|<span data-ttu-id="a701e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a701e-105">Method</span></span>|<span data-ttu-id="a701e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a701e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a701e-107">GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="a701e-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="a701e-108">Získá ukazatel rozhraní na implementaci rozhraní se zadaným `IID`.</span><span class="sxs-lookup"><span data-stu-id="a701e-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="a701e-109">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="a701e-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="a701e-110">Upozorňuje hostitele, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="a701e-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a701e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a701e-111">Requirements</span></span>  
 <span data-ttu-id="a701e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a701e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a701e-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a701e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a701e-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a701e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a701e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a701e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a701e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a701e-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="a701e-117">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a701e-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="a701e-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a701e-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a701e-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a701e-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
