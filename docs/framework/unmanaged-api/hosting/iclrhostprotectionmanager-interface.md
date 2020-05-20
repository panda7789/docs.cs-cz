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
ms.openlocfilehash: 7b1fc70380fff3c551c56043f49c2deda507e366
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703837"
---
# <a name="iclrhostprotectionmanager-interface"></a><span data-ttu-id="a033c-102">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a033c-102">ICLRHostProtectionManager Interface</span></span>
<span data-ttu-id="a033c-103">Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ze spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="a033c-103">Enables the host to block specific managed classes, methods, properties, and fields from running in partially trusted code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a033c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a033c-104">Methods</span></span>  
  
|<span data-ttu-id="a033c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a033c-105">Method</span></span>|<span data-ttu-id="a033c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a033c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a033c-107">SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="a033c-107">SetEagerSerializeGrantSets</span></span>](iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|<span data-ttu-id="a033c-108">Poskytuje záruku, že některé vzácné konflikty časování, které mohou způsobit závažné chyby modulu CLR (Common Language Runtime), nebudou nikdy nastat.</span><span class="sxs-lookup"><span data-stu-id="a033c-108">Provides a guarantee that certain rare race conditions that can cause fatal common language runtime (CLR) errors will never arise.</span></span>|  
|[<span data-ttu-id="a033c-109">SetProtectedCategories – metoda</span><span class="sxs-lookup"><span data-stu-id="a033c-109">SetProtectedCategories Method</span></span>](iclrhostprotectionmanager-setprotectedcategories-method.md)|<span data-ttu-id="a033c-110">Určuje kategorie spravovaných typů a členů, které mají být zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="a033c-110">Specifies the categories of managed types and members that should be blocked from running in partially trusted code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a033c-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a033c-111">Requirements</span></span>  
 <span data-ttu-id="a033c-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a033c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a033c-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a033c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a033c-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a033c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a033c-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a033c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a033c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a033c-116">See also</span></span>

- [<span data-ttu-id="a033c-117">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="a033c-117">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="a033c-118">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a033c-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
