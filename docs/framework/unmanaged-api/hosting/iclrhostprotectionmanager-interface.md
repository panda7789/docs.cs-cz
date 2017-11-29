---
title: "ICLRHostProtectionManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager
helpviewer_keywords: ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c88279eb26b819adaaaf86dcf59105c6ac728017
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="3c382-102">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c382-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="3c382-103">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ve spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="3c382-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c382-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3c382-104">Methods</span></span>  
  
|<span data-ttu-id="3c382-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3c382-105">Method</span></span>|<span data-ttu-id="3c382-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3c382-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c382-107">Seteagerserializegrantsets –</span><span class="sxs-lookup"><span data-stu-id="3c382-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="3c382-108">Poskytuje záruku, že se nikdy vynoří určité výjimečných časování, které mohou způsobit závažné common language runtime (CLR) chyby.</span><span class="sxs-lookup"><span data-stu-id="3c382-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="3c382-109">Setprotectedcategories – metoda</span><span class="sxs-lookup"><span data-stu-id="3c382-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="3c382-110">Určuje kategorie spravované typy a členy, kteří mají blokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="3c382-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3c382-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3c382-111">Requirements</span></span>  
 <span data-ttu-id="3c382-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c382-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c382-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c382-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c382-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c382-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c382-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c382-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c382-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c382-116">See Also</span></span>  
 [<span data-ttu-id="3c382-117">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="3c382-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [<span data-ttu-id="3c382-118">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3c382-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
