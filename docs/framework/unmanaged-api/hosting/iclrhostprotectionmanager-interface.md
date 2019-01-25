---
title: ICLRHostProtectionManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4cb310215967a79e43e43319e107b6c42551e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557432"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="4a83a-102">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a83a-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="4a83a-103">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="4a83a-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a83a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4a83a-104">Methods</span></span>  
  
|<span data-ttu-id="4a83a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4a83a-105">Method</span></span>|<span data-ttu-id="4a83a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4a83a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a83a-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="4a83a-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="4a83a-108">Poskytuje záruku, že se nikdy vznikají některých výjimečných časování, které mohou způsobit závažná common language runtime (CLR) chyby.</span><span class="sxs-lookup"><span data-stu-id="4a83a-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="4a83a-109">SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="4a83a-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="4a83a-110">Určuje kategorie spravované typy a členy, které by měl být blokovaný spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="4a83a-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a83a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a83a-111">Requirements</span></span>  
 <span data-ttu-id="4a83a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a83a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a83a-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a83a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a83a-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a83a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a83a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a83a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a83a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a83a-116">See also</span></span>
- [<span data-ttu-id="4a83a-117">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="4a83a-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="4a83a-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a83a-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
