---
title: IAppDomainBinding – rozhraní
ms.date: 03/30/2017
api_name:
- IAppDomainBinding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainBinding
helpviewer_keywords:
- IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2c3a3057003d0035bfcb096a94c84d610e3056f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134183"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="05ed8-102">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ed8-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="05ed8-103">Poskytuje metodu, která je volána modulem common language runtime (CLR), která upozorní aplikaci hostitele Vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="05ed8-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05ed8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="05ed8-104">Methods</span></span>  
  
|<span data-ttu-id="05ed8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="05ed8-105">Method</span></span>|<span data-ttu-id="05ed8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="05ed8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05ed8-107">OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="05ed8-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="05ed8-108">Volána modulem common language runtime (CLR), aby upozornil hostitele Vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="05ed8-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05ed8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05ed8-109">Requirements</span></span>  
 <span data-ttu-id="05ed8-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ed8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ed8-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05ed8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05ed8-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05ed8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05ed8-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ed8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ed8-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05ed8-114">See also</span></span>

- [<span data-ttu-id="05ed8-115">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="05ed8-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
