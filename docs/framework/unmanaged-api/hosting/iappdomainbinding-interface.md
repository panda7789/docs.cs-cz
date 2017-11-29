---
title: "IAppDomainBinding – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainBinding
helpviewer_keywords: IAppDomainBinding interface [.NET Framework hosting]
ms.assetid: 368881ab-c4ea-4731-bf22-c596aac7c66c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e02c1b9499bc2972f88c9045d3f59423edb6cb2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="6d2cf-102">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6d2cf-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="6d2cf-103">Poskytne metodu, která je volána metodou modul CLR (CLR) oznámit hostitelskou aplikaci vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d2cf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d2cf-104">Methods</span></span>  
  
|<span data-ttu-id="6d2cf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d2cf-105">Method</span></span>|<span data-ttu-id="6d2cf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6d2cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d2cf-107">Onappdomain – metoda</span><span class="sxs-lookup"><span data-stu-id="6d2cf-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="6d2cf-108">Voláno rozhraním modul CLR (CLR) oznámit hostitele vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6d2cf-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d2cf-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6d2cf-109">Requirements</span></span>  
 <span data-ttu-id="6d2cf-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2cf-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6d2cf-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d2cf-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d2cf-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d2cf-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2cf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d2cf-114">See Also</span></span>  
 [<span data-ttu-id="6d2cf-115">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="6d2cf-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
