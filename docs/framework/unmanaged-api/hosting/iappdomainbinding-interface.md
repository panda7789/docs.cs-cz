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
ms.openlocfilehash: a6761ff204d299bc2db84e2e80d988306125a110
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430818"
---
# <a name="iappdomainbinding-interface"></a><span data-ttu-id="f9151-102">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9151-102">IAppDomainBinding Interface</span></span>
<span data-ttu-id="f9151-103">Poskytne metodu, která je volána metodou modul CLR (CLR) oznámit hostitelskou aplikaci vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9151-103">Provides a method that is called by the common language runtime (CLR) to notify the host application that an application domain has been created.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9151-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f9151-104">Methods</span></span>  
  
|<span data-ttu-id="f9151-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9151-105">Method</span></span>|<span data-ttu-id="f9151-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f9151-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9151-107">OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="f9151-107">OnAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-onappdomain-method.md)|<span data-ttu-id="f9151-108">Voláno rozhraním modul CLR (CLR) oznámit hostitele vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9151-108">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f9151-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9151-109">Requirements</span></span>  
 <span data-ttu-id="f9151-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9151-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9151-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f9151-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f9151-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f9151-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9151-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9151-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9151-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9151-114">See Also</span></span>  
 [<span data-ttu-id="f9151-115">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f9151-115">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
