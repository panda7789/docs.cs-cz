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
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703526"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="7347d-102">ICLRMetaHostPolicy – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7347d-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="7347d-103">Poskytuje metodu [GetRequestedRuntime –](iclrmetahostpolicy-getrequestedruntime-method.md) , která vrací ukazatel na rozhraní modulu CLR (Common Language Runtime) na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7347d-103">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7347d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7347d-104">Methods</span></span>  
  
|<span data-ttu-id="7347d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7347d-105">Method</span></span>|<span data-ttu-id="7347d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7347d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7347d-107">GetRequestedRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="7347d-107">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="7347d-108">Poskytuje preferované rozhraní CLR na základě kritérií zásad, spravovaného sestavení, verze a konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7347d-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7347d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7347d-109">Remarks</span></span>  
 <span data-ttu-id="7347d-110">Můžete získat odkaz na toto rozhraní voláním funkce [CLRCreateInstance –](clrcreateinstance-function.md) , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="7347d-110">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="7347d-111">Toto rozhraní ve skutečnosti nenačítá nebo neaktivuje modul CLR, ale jednoduše vrátí preferovanou verzi CLR na základě dostupných verzí, které jsou nainstalovány nebo načteny.</span><span class="sxs-lookup"><span data-stu-id="7347d-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="7347d-112">Rozhraní API pro .NET Framework 4 konsoliduje zásady, aby hostitelé s konkrétními požadavky mohli používat základní funkce, aniž by museli vymezit nezamýšlené pokuty.</span><span class="sxs-lookup"><span data-stu-id="7347d-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="7347d-113">Například mnohé z exportů MSCorEE. dll se budou navazovat na konkrétní CLR, i když ji metoda nemusí logicky vyžadovat.</span><span class="sxs-lookup"><span data-stu-id="7347d-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="7347d-114">Výčet [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) poskytuje zásady vazeb, které jsou společné pro většinu hostitelů.</span><span class="sxs-lookup"><span data-stu-id="7347d-114">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7347d-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7347d-115">Requirements</span></span>  
 <span data-ttu-id="7347d-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7347d-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7347d-117">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7347d-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7347d-118">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7347d-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7347d-119">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7347d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7347d-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7347d-120">See also</span></span>

- [<span data-ttu-id="7347d-121">Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5</span><span class="sxs-lookup"><span data-stu-id="7347d-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="7347d-122">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7347d-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7347d-123">Hostování</span><span class="sxs-lookup"><span data-stu-id="7347d-123">Hosting</span></span>](index.md)
