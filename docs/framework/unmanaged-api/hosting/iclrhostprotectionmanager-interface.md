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
ms.openlocfilehash: 0487a87420c888cf5466f54c28c2d89623260add
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141047"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="54c6d-102">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54c6d-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="54c6d-103">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ze spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="54c6d-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54c6d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="54c6d-104">Methods</span></span>  
  
|<span data-ttu-id="54c6d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="54c6d-105">Method</span></span>|<span data-ttu-id="54c6d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="54c6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54c6d-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="54c6d-107">SetEagerSerializeGrantSets</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="54c6d-108">Poskytuje záruku, že některé vzácné konflikty časování, které mohou způsobit závažné chyby modulu CLR (Common Language Runtime), nebudou nikdy nastat.</span><span class="sxs-lookup"><span data-stu-id="54c6d-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="54c6d-109">SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="54c6d-109">SetProtectedCategories Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="54c6d-110">Určuje kategorie spravovaných typů a členů, které mají být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="54c6d-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54c6d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="54c6d-111">Requirements</span></span>  
 <span data-ttu-id="54c6d-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c6d-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="54c6d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54c6d-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54c6d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54c6d-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c6d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c6d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54c6d-116">See also</span></span>

- [<span data-ttu-id="54c6d-117">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="54c6d-117">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="54c6d-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="54c6d-118">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
