---
title: ICLRMetaHostPolicy – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426d77114d3deeff94c39e2f5fc1f2e56e753641
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490272"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="e24a4-102">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e24a4-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="e24a4-103">Poskytuje [getrequestedruntime –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodu, která vrací ukazatel na obecné rozhraní language runtime (CLR) na základě kritérií zásad, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="e24a4-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e24a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e24a4-104">Methods</span></span>  
  
|<span data-ttu-id="e24a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e24a4-105">Method</span></span>|<span data-ttu-id="e24a4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e24a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e24a4-107">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="e24a4-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="e24a4-108">Poskytuje preferovaným rozhraním CLR na základě kritérií zásad, spravované sestavení, verzi a konfiguračnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="e24a4-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e24a4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e24a4-109">Remarks</span></span>  
 <span data-ttu-id="e24a4-110">Odkaz na toto rozhraní můžete získat voláním [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat tak, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="e24a4-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="e24a4-111">Toto rozhraní není ve skutečnosti načíst nebo aktivovat CLR, ale jednoduše vrátí upřednostňovanou verzi CLR na základě dostupné verze, které jsou nainstalovány nebo načtena.</span><span class="sxs-lookup"><span data-stu-id="e24a4-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="e24a4-112">Rozhraní .NET Framework 4, který je hostitelem rozhraní API konsoliduje zásady tak, aby hostitelé s konkrétním potřebám mohou používat základní funkce bez dalších nákladů na nežádoucí následky.</span><span class="sxs-lookup"><span data-stu-id="e24a4-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="e24a4-113">Například řadu exporty MSCorEE.dll vytvoří vazbu na konkrétní CLR, i když metody nemusí stačit logicky ho.</span><span class="sxs-lookup"><span data-stu-id="e24a4-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="e24a4-114">[Metahost_policy_flags –](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) výčet poskytuje zásady vazby, které jsou společné pro většinu hostitele.</span><span class="sxs-lookup"><span data-stu-id="e24a4-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e24a4-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e24a4-115">Requirements</span></span>  
 <span data-ttu-id="e24a4-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e24a4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e24a4-117">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e24a4-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e24a4-118">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e24a4-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e24a4-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e24a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24a4-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e24a4-120">See also</span></span>

- [<span data-ttu-id="e24a4-121">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="e24a4-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="e24a4-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="e24a4-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e24a4-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="e24a4-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
