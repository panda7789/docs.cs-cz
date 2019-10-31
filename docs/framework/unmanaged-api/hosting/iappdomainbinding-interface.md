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
ms.openlocfilehash: cf4fa9c5ec35391a0e772e25112f305bfa6e1564
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126892"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="0e35d-102">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0e35d-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="0e35d-103">Poskytuje metodu, která je volána modulem CLR (Common Language Runtime), aby upozornila hostitelskou aplikaci, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e35d-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e35d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e35d-104">Methods</span></span>  
  
|<span data-ttu-id="0e35d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e35d-105">Method</span></span>|<span data-ttu-id="0e35d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0e35d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e35d-107">OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="0e35d-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="0e35d-108">Volána modulem CLR (Common Language Runtime) pro oznamování hostitele, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e35d-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e35d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e35d-109">Requirements</span></span>  
 <span data-ttu-id="0e35d-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e35d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e35d-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e35d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e35d-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e35d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e35d-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e35d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e35d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e35d-114">See also</span></span>

- [<span data-ttu-id="0e35d-115">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0e35d-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
