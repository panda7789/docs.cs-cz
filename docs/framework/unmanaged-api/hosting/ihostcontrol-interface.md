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
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804937"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="6b800-102">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b800-102">IHostControl Interface</span></span>
<span data-ttu-id="6b800-103">Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.</span><span class="sxs-lookup"><span data-stu-id="6b800-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b800-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6b800-104">Methods</span></span>  
  
|<span data-ttu-id="6b800-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6b800-105">Method</span></span>|<span data-ttu-id="6b800-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6b800-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b800-107">GetHostManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6b800-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="6b800-108">Získá ukazatel rozhraní na implementaci rozhraní se zadaným hostitelem `IID` .</span><span class="sxs-lookup"><span data-stu-id="6b800-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="6b800-109">SetAppDomainManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6b800-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="6b800-110">Upozorňuje hostitele, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b800-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b800-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b800-111">Requirements</span></span>  
 <span data-ttu-id="6b800-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b800-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b800-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b800-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b800-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b800-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b800-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b800-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b800-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b800-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="6b800-117">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b800-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="6b800-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b800-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="6b800-119">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6b800-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
