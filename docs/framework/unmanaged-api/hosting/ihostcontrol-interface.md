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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 014e5c9951091046ae07374794743e82affcd5ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967726"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="afe62-102">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afe62-102">IHostControl Interface</span></span>
<span data-ttu-id="afe62-103">Poskytuje metody pro konfiguraci načítání sestavení a k určení, kterou rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="afe62-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afe62-104">Metody</span><span class="sxs-lookup"><span data-stu-id="afe62-104">Methods</span></span>  
  
|<span data-ttu-id="afe62-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="afe62-105">Method</span></span>|<span data-ttu-id="afe62-106">Popis</span><span class="sxs-lookup"><span data-stu-id="afe62-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afe62-107">GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="afe62-107">GetHostManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="afe62-108">Získá ukazatel rozhraní k implementaci rozhraní hostitele se zadanou `IID`.</span><span class="sxs-lookup"><span data-stu-id="afe62-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="afe62-109">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="afe62-109">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="afe62-110">Upozorňuje hostitele, vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="afe62-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="afe62-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afe62-111">Requirements</span></span>  
 <span data-ttu-id="afe62-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afe62-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe62-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="afe62-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afe62-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afe62-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afe62-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe62-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe62-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afe62-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="afe62-117">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afe62-117">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="afe62-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="afe62-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="afe62-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="afe62-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
